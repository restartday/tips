### publish 로 빌드 후 
### appsettings.json에 아래 항목 추가
~~~json
"Kestrel": {
  "EndPoints": {
    "Http": {
      "Url": "http://0.0.0.0:5002"
    },
    "Https": {
    "Url": "https://0.0.0.0:5003"
    }
  }
}
~~~
또는

"Urls": "http://0.0.0.0:5001;https://0.0.0.0:5002"
추가
 

### dotnet run시 - project 소스폴더에서 실행시
Properties디렉토리 아래 launchSettings.json에
~~~json
"profiles": {
    "projectName": {     //Project Name
      "commandName": "Project",
      "launchBrowser": true,
      "environmentVariables": {
        "ASPNETCORE_ENVIRONMENT": "Development"
      },
      "applicationUrl": "https://localhost:5001;http://localhost:5000"
    }
  }
~~~
