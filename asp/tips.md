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
