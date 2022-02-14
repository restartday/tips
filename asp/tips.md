file upload web api  
https://tocalai.medium.com/upload-download-file-s-in-asp-net-core-1fa89166aab0

Web Api argument Bind
~~~cs
[HttpPost]
[Route("/api/whats")]  //absolute
public IActionResult Post([FromForm(Name = "name")] string fileName, [FromForm(Name = "file")]IFormFile file)
{
  return ok();
  return NoContent();
}
~~~

Web Api Ip Restrict 
https://stackoverflow.com/questions/49321619/how-to-make-a-route-accessible-only-from-localhost
~~~cs
public class RestrictToLocalhostAttribute : ActionFilterAttribute
{
    public override void OnActionExecuting(ActionExecutingContext context)
    {
        var remoteIp = context.HttpContext.Connection.RemoteIpAddress;
        if (!IPAddress.IsLoopback(remoteIp)) {
            context.Result = new UnauthorizedResult();
            return;
        }
        base.OnActionExecuting(context);
    }
}

[Route("api/elasticsearch/resync/products")]
[HttpGet]
[RestrictToLocalhost]
public async Task<string> ResyncProducts()
{
}

~~~

port block in Configure 
~~~cs
public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
{
    if (env.IsDevelopment())
    {
        app.UseDeveloperExceptionPage();
        app.UseWebAssemblyDebugging();
    }
    else
    {
        app.UseExceptionHandler("/Error");
        // The default HSTS value is 30 days. You may want to change this for production scenarios, see https://aka.ms/aspnetcore-hsts.
        app.UseHsts();
    }

    app.Use(async (context, next) =>
    {
        if (context.Connection.LocalPort == 5001)
        {
            context.Response.StatusCode = 400;
            await context.Response.CompleteAsync();
        }
        else
        // Call the next delegate/middleware in the pipeline.
            await next(context);
    });
    app.UseStaticFiles();

    app.UseRouting();
}
~~~
