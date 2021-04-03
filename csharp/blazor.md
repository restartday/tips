Clipboard in .razor  
~~~cs
@inject IJSRuntime JS;

<button @onclick='() => { JS.InvokeVoidAsync("navigator.clipboard.writeText", "text");}'>Clipboard</button>
~~~
