
Visual Studio project에 Debug시 마운트하기  
~~~
<DockerfileRunArguments>-v c:\temp:/root/temp</DockerfileRunArguments>
~~~

Docker run 옵션  
~~~
--name //containerName
-p 1000:1000   //포트 포워딩(외부/컨테이너순)
-e HOME=/home   //envirment할당
~~~

Docker build 옵션
~~~
docker build -f 파일이름 -t 이미지 이름 .
~~~
