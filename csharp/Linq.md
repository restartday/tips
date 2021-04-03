
foreach로 index  
~~~cs 
List<string> datas = new List<string> { "a", "b", "c" };
foreach (var data in dats.Select((v,i) => new { v, i }))
{
  var value = data.b;
  var index = data.i;
}
~~~
