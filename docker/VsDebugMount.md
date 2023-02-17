
Visual Studio project에 Debug시 마운트하기  
~~~
<DockerfileRunArguments>-v c:\temp:/root/temp</DockerfileRunArguments>
~~~

Docker run 옵션  
~~~
--name //containerName
-p 1000:1000   //포트 포워딩(외부/컨테이너순)
-e HOME=/home   //envirment할당
 --add-host host.docker.internal:host-gateway //Ubuntu에서 내부에서 localhost접근하고 싶을때 host.docker.internal에 매핑
~~~

Docker build 옵션
~~~
docker build -f 파일이름 -t 이미지 이름 .
~~~

Docker Vscode Tips   
https://blog.mastykarz.nl/docker-containers-visual-studio-code-extension/


Arm ubuntu docker 안될때
~~~
1. Delete everything in /var/lib/docker. 
   This will delete existing container and images:

rm -rf /var/lib/docker

2. Then configure your daemon to use the "overlay" storage driver. 
Set the following flags in /etc/docker/daemon.json. 
If the file doesn't exist, just create it, and add the contents below:
{
    "graph": "/mnt/docker-data",
    "storage-driver": "overlay"
}

3. Docker Restart
https://stackoverflow.com/questions/39100641/docker-service-start-failed
~~~

