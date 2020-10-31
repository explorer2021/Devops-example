# Installing Docker on Amazon Linux server

### Pre-requisites
1. Amazon Linux EC2 Instance

## Installation Steps

1. Install docker and start docker services
   ```sh 
   yum install docker -y
   docker --version 
   
   # start docker services
   service docker start
   service docker status
   ```
1. Create a user called dockeradmin
   ```sh
   useradd dockeradmin
   passwd dockeradmin
   ```
1. add a user to docker group to manage docker 
   ```
   usermod -aG docker dockeradmin
   ```
### Validation test
1. Create a tomcat docker container by pulling a docker image from the public docker registry
   ```sh
   docker pull tomcat:latest
   docker image ls
   docker run -d --name test-tomcat-server -p 8080:8080 tomcat:latest
   ```
2. Check if Docker image is created correctly or not ?
   ```sh
   [root@Docker-HOST ~]# docker image ls
   REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
   tomcat              latest              625b734f984e        8 days ago          648MB
    ```
3. Check if Docker container is created correctly or not ?
   ```sh
   root@Docker-HOST ~]# docker ps -a
   CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS                    NAMES
   a397e05b5fad        tomcat:latest       "catalina.sh run"   9 minutes ago       Up 9 minutes        0.0.0.0:8080->8080/tcp   test-tomcat-server
   ```
4. if you receiver HTTP status 404-Not Found Error, Login to Docker Image and correct webapps folder
   ```sh
   docker exec -it test-tomcat-server /bin/bash
   root@a397e05b5fad:/usr/local/tomcat# cp -r webapps.dist/* ./webapps
   ```

 
