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
