Docker Crash Course for Absolute Beginners

https://www.youtube.com/watch?v=pg19Z8LL06w

https://raw.githubusercontent.com/RodrigoMvs123/Docker-Crash-Course-for-Absolute-Beginners/main/README.md

https://docs.docker.com/get-docker/


1 - What and Why is Docker ?
What is Docker
What problems does it solve ?
Software Development before and after Docker
Software Deployment before and after Docker 
2 - Docker versus Virtual Machines 
Understand the difference of Docker and VM 
Benefits of Docker 
3 - Install Docker locally 
4 - Images versus Containers 
5 - Public and Private Registries 
6 - Run Containers 
Pull and run containers from public repository 
Port Binding, Detached Mode etc
7 - Create own Image (Dockerfile)
Syntax and concepts of Dockerfile
We will dockerize a Node.js app 
8 - Main Docker commands 
pull
run
start
stop
logs
build
9 - Image Versioning 
10 - Docker Workflow Big Picture 

[
Docker Hub
Developing a JS app
Commit 
Git
Trigger CI/CD 

CI Server 
Builds Docker Image
JavaScript 

Push 
Private Repository 
Pull

Deployment Server 
Both images are pulled on the server 
JavaScript - Image 

Docker hub 
Pull 
]


What is Docker ?
Why was it created ? 
What problems does it solve ? 

What is Docker ?
Virtualization Software 
Makes developing and deploying applications much easier 
Packages applications with all necessary dependencies, configuration, system tools and runtime 
Container 
A standardized unit, that has everything the application needs to run 
Portable artifact, easily shared and distributed 

What problems does Docker solve ? 
Development process before containers ?
Each developer needs to install and configure all services directly on their OS on their local machine 
Installation process different for each OS environment 
Many steps, where something can go wrong 
If your app uses 10 services, each developer needs to install these 10 services


Own isolated environment 
Postgres package with all dependencies and configurations 
Start service as a Docker container using a 1 Docker Command 
Command same for all OS  
Standardized process of running any service on any local developer environment 
Docker run postgres
Docker run redis 
Docker run … 

Easy to run different versions of same app without any conflicts 


Deployment process before containers 
Artifact 
Installation instructions 
How to install and configure apps on the server ? 
JAR 
Database 
How to install and configure apps on the server ? 
Artifacts and instructions handed over to operations team
Operations team handles installing and configuring apps and its dependencies 
Installations and configurations done directly on the server's Operational Systems 
Dependency version conflicts etc
Miscommunications DEVOPS 
Textual guide of development 
Human errors can happen 
Back and forth communication 


Configuration 
App source code - JAR 
Dependencies 
Artifact of Docker 
Docker artifact includes everything the app needs

Instead of textual, everything is packaged inside the Docker artifact 
No configurations needed on the server ( Except Docker runtime )
Less room for errors 
Run Docker command to fetch and run the Docker artifacts 
Artifact of Docker 


Virtual Machine versus Docker

Docker 
Virtualization Tool 
Virtual Machine 
Why is Docker so widely used ?
What advantages does it have over Virtual Machines ?
What are the differences ? 

How does Docker run its containers ? 
How an Operational System is made up
OS applications Layers 

OS Kernel  
Hardware - CPU / Memory / 
Kernel is at the core of every operating system 
OS applications Layers 
Kernel interacts between hardware and software components
Docker and Virtual Machines 
Both are virtualization tools 

What parts of the OS do they virtualize ? 

Docker 
Docker virtualize the OS Applications Layers 
Contains the OS applications Layers 
Services and apps installed on top that layer 
Virtual Machine 
OS Applications Layer
OS Kernel 

Physical Machine 
Host OS 
VM             VM 
app A         app B
Guest OS   Guest OS 

Physical Machine 
Host OS
Docker
App A       App B

Docker
Size
Docker images much smaller 
Docker images, couple of MB 
Speed
Containers take seconds to start 
Compatibility 
Compatible only with Linux distros 

VM
Size
VM images, couple of GB 
Speed
VMs take minutes to start
Compatibility 
VM is compatible with all OS 


Compatibility 

Docker
Applications Linux
Linux based Docker images, cannot use Windows kernel 

Applications 
OS Kernel 
Hardware 

Most containers are linux based 
Originally built for linux OS 

Docker Desktop 
Allows you to run Linux containers on Windows or MacOS  
Uses a hypervisor layer with a light lightweight Linux distro 
Install Docker Desktop 

Install Docker 
Install docker on your local machine 
Go to the official Docker website 
Follow installation steps 
https://docs.docker.com/desktop/install/windows-install/

Docker Desktop includes 
Docker Engine 
A serve with a long-running daemon process “dockerd”‘
Manages images and containers 
Docker CLI - Client 
Command Line Interface (“Docker”) to interact with Docker Server 
Execute Docker commands to start / to stop / .. containers 
Graphical user interface client (GUI)
To manage your containers and images with a graphical user interface

What are images ? 
What is an Image compared to a Container ? 

Docker Images versus Docker Containers 
Package the applications with its environment configuration 
Package everything into a artifact 

Share 
Can be easily shared and moved 
Like a zip or tar file or jar file    
Artifact 
Artifact Repository 
Download on the server or locally

Docker Image 
An executable application artifact 
Includes app source code, but also complete environment configuration 
Add environment variables, create directories, files etc 


Application                 JS app 
Any services needed  node npm 
OS Layer                    Linux 
Directories 
Files 

Docker Container 
Actually starts the application 
Package (www)          Image 
Download to server 
Or local computer 
It will be runned on the OS of the computer 
Container 
Running Instance of an image 

Image 
You can run multiple containers from 1 image 

Images on Disk 
Application Packages 
Containers / App
Running Instances of those image 

Terminal 
[/W]$ docker images 
Docker images = List all Docker images 
Repository    TAG      IMAGE ID      CREATED      SIZE 
[/W]$ Docker ps 
Docker ps = List running containers 
CONTAINER ID     IMAGE     COMMAND     CREATED     STATUS      PORTS     NAMES
[/W]$ 

https://www.nethopper.io/
https://www.nethopper.io/kaops-platform
DevOps 
KAOps 
Kubernetes Application Operations Platform 
Multi-Cloud ( or virtual ) 
Application Network 
Google Cloud 
AWS 
Azure 
https://mynethopper.com/networks

Docker Registry
A storage and distribution system for Docker images 
Run containers from images 
How do we get these images ?
Official Images available from applications like Redis, Mongo, Postgre etc 
Official Images are maintained by the software authors or in collaboration with the Docker community 
Docker Hub 
Docker hosts one of the biggest Docker Registry, called “Docker Hub”
Find and share Docker Images 
https://hub.docker.com/

Docker Official Images 
A dedicated team responsible for reviewing and publishing all content in the Docker Official Images repository 
Works in collaboration with software maintainers, security experts 
However anyone can participate as collaboration takes place openly on GitHub 


Image Versioning 

Technology changes .. 
redis:6.0.17   redis: 6.2.10   redis:7.0.8

Image            Image           Image
redis: 6.0.x.   redis: 6.2.x   redis: 7.0.x

Docker images are versioned 
Different versions are identified by tags 
Docker tags are used to identify images by name 
“latest” tag mostly refers to the newest release 

Pull an Image 
https://hub.docker.com/_/nginx
Using a specific version is best practice in most cases
[/W]$ docker pull nginx 
docker pull {name}:{Tag} = Pull an image from a registry 
Version 
https://hub.docker.com/_/nginx
1.23
 
Docker Hub 
image 
nginx:1.23 

User 
# Download locally 
[/W]$ docker pull nginx 
# docker.io/library/nginx:1.23
[/W]$ docker images
REPOSITORY        TAG        IMAGE ID         CREATED        SIZE       
nginx                       1.23        a99a39d070bf   4 days ago       142MB
[/W]$ docker pull nginx 
# Using default tag : latest 
[/W]$ docker images 
# Images locally 
nginx                       1.23        a99a39d070bf   4 days ago       142MB
nginx                       latest      a99a39d070bf   4 days ago       142MB
[/W]$ 

Run an Image 
[/W]$ docker run nginx: 1.23 
# Start worker process 
[/W]$ docker ps 
# Container ID         IMAGE         COMMAND            CREATED 
# Tus                        PORTS        NAMES 
# 9b1f9ce192bf        nginx: 1.23   “ /docker…              About a minute ago 
# About a minute      80/tcp          awesome_volhard 
[/W]$ control c 
       exit
[/W]$ docker ps 
CONTAINER ID       IMAGE    COMMAND   CREATED   STATUS   PORTS    NAMES 
[/W]$ docker run -d nginx:1.23
# -d or - - detach = Runs container in background  and prints the container ID 

ea49e4f0fd7… 
[/W]$ docker ps 
CONTAINER ID         IMAGE       COMMAND                       CREATED        STATUS 
                   PORTS    NAMES 
ea49e4f0fd7…                nginx:1.23   “/docker-entrypoint …”      33 seconds ago Up 32 
seconds     80/tcp      friendly_yalow
# You may still want to see the logs, which can be useful for debugging etc 
[/W]$ docker logs ea49e4f0fd7… 
# docker logs {container} = View logs from service running inside the container. (which are present at the time of execution)

docker hub
                    image 
                 nginx:1.23
docker run 
# Docker pulls image automatically, if it does not find it locally 

[/W]$ docker images 
REPOSITORY         TAG          IMAGE ID         CREATED        SIZE  
nginx                        1.23         a99a39d070bf    4 days ago      142MB 
nginx                        latest       a99a39d070bf     4 days ago      142MB

[/W]$ docker run nginx:1.22-alpine 
# unable to find image ‘nginx:1.22-alpine’ locally 

[/W]$ docker ps 
CONTAINER ID       IMAGE       COMMAND     CREATED      STATUS      PORTS    NAMES
fc602bb99b7d   nginx:1.22-alpin “/docker-entry 38 seconds ago                 80/tcp fervent_bardeen                       
ea491e4f0fd7    nginx:1.23          “/docker-entry  5 minutes ago                   80/tcp     friendly_yalow 
[/W]$ docker ps 
CONTAINER ID       IMAGE       COMMAND     CREATED      STATUS      PORTS    NAMES
ea491e4f0fd7           nginx:1.23    “/docker-entry 7 minutes ago up 7 minutes 80/tcp friendly_yalow 
[/W]$ 
Without connection 
Port 80/tcp
Image nginx:1.23
localhost:80

Port Binding 
Container Port versus Host Port 
Container nginx Port 80 ( No www access ) 
Application inside container runs in an isolated Docker network 
This allows us to run the same app running on the same port multiple times 
We need to expose the container port to the host ( The machine the container runs on )
Host 
Container 
nginx 
Port 80 
www
Port Binding: Bind the container´s port to the host´s port to make the service available to the outside world 

Container runs on a specific port 
- Host ( Your Laptop ) 
Container
nginx 
Port 80

Container 
Redis 
Port 6379 

Publish container´s port to the host 
localhost 
Container 
nginx 
Port 80 
Port 9000 

[/W]$ docker stop ea491e4f0fd7  # running container ea491e4f0fd7 
# docker stop {container} = Stop one or more running containers 
# ea491e4f0fd7  
[/W]$ docker run -d -p 9000:80 nginx:1.23 
# -p or - - publish = publish a container's port to the host 
# -p {HOST_PORT}:{CONTAINER_PORT}
70adc073cfc2bb122e5bbd6796c1ad34fbb24e4572509c2704ca02cde683
[/W]$ docker ps 
CONTAINER ID       IMAGE       COMMAND     CREATED      STATUS      PORTS    NAMES
#70adc073cfc2         nginx:1.23   /docker-entry… 4 seconds ago Up 4 secon… 0.0.0.0:9000->80/tcp, :::9000->80/tcp beautiful_saha 
# Only 1 service can run on a specific port on the host 
# Only 1 service can run on port 9000
# localhost:9000 ( Welcome to nginx page ) 
[/W]$ docker logs 70adc073cfc2 

Choosing host port 
localhost 
MySQL
Port 3306
Port 3306
# Standard to use the same port on your host as container is using

Start and stop containers 
Docker run 
Creates a new container 
Does not re-use previous container
Docker run
Docker run
Docker run 
Docker run 
[/W]$ docker ps 
#CONTAINER ID       IMAGE       COMMAND     CREATED      STATUS      PORTS    #NAMES
#70adc073cfc2         nginx:1.23   /docker-entry… 4 seconds ago Up 4 secon… #0.0.0.0:9000->80/tcp, :::9000->80/tcp beautiful_saha 
[/W]$ docker ps -a 
# -a or - - all = Lists all containers ( stopped and running ) 
#CONTAINER ID       IMAGE       COMMAND     CREATED      STATUS      PORTS    #NAMES
#70adc073cfc2         nginx:1.23   /docker-entry… 4 seconds ago Up 4 secon… #0.0.0.0:9000->80/tcp, :::9000->80/tcp beautiful_saha 
#CONTAINER ID       IMAGE       COMMAND     CREATED      STATUS      PORTS    #NAMES
#fc602bb99b7d   nginx:1.22-alpin “/docker-entry 38 seconds ago                 80/tcp #fervent_bardeen           
#CONTAINER ID       IMAGE       COMMAND     CREATED      STATUS      PORTS    #NAMES
#ea491e4f0fd7    nginx:1.23          “/docker-entry  5 minutes ago                   80/tcp     #friendly_yalow 
# Container ID         IMAGE         COMMAND            CREATED 
# Tus                        PORTS        NAMES 
# 9b1f9ce192bf        nginx: 1.23   “ /docker…              About a minute ago 
# About a minute      80/tcp          awesome_volhard 
[/W]$ docker stop 70adc073cfc2 
[/W]$ docker ps -a
#CONTAINER ID       IMAGE       COMMAND     CREATED      STATUS      PORTS    #NAMES
#70adc073cfc2         nginx:1.23   /docker-entry… 4 seconds ago Up 4 secon… 
#0.0.0.0:9000->80/tcp, :::9000->80/tcp beautiful_saha 
# docker start { container } = Start one or more stopped containers 
[/W]$ docker start 70adc073cfc2
#70adc073cfc2
[/W]$ docker start fc602bb99b7d
#fc602bb99b7d
[/W]$ docker ps 
#CONTAINER ID       IMAGE       COMMAND     CREATED      STATUS      PORTS    #NAMES
#70adc073cfc2         nginx:1.23   /docker-entry… 4 seconds ago Up 4 secon… #0.0.0.0:9000->80/tcp, :::9000->80/tcp beautiful_saha 
#CONTAINER ID       IMAGE       COMMAND     CREATED      STATUS      PORTS    #NAMES
#fc602bb99b7d   nginx:1.22-alpin “/docker-entry 38 seconds ago                 80/tcp #fervent_bardeen   
[/W]$ docker stop 70adc073cfc2 fervent_bardeen   
#70adc073cfc2
#fervent_bardeen   
[/W]$ docker ps 
#CONTAINER ID       IMAGE       COMMAND     CREATED      STATUS      PORTS    #NAMES
[/W]$ docker run --name web app -d -p 9000:80 nginx:1.23
# - - name = Assign a name to the container 
a22f17e005356f4501c57f7b045921148820afb9f94c8e41b4e9708cb1402193
[/W]$ docker ps 
#CONTAINER ID       IMAGE       COMMAND     CREATED      STATUS      PORTS    #NAMES
#a22f17e00535         nginx:1.23   “/docker-entry…3 seconds ago Up 2 seconds #0.0.0.0:9000->80/tcp, :::9000->80tcp web-app
[/W]$ docker logs web-app

Private Docker Registries 

Public and Private Docker Registries 
Docker Hub 
Public
Image Registry 
Largest public registry
Anyone can search and download Docker images 

Companies 
Image 
Docker Hub
my-app 
Private Docker Registry 
You need to authenticate before accessing the Registry 
All big cloud provider offer private registries: Amazon ECR (Elastic Container Registry), Google Container Registry, etc
AWS
Google Cloud 
Microsoft Azure 
Nexus (popular artifact repository manager)
Docker hub 


Registry versus Repository 
Docker Registry 

AWS ECR
my-service 
my-app

A service providing storage 
Can be hosted by a third party, like AWS, or by yourself 
Collection of repositories 

Docker Repository 
Collection of related images with same name but different versions 
AWS ECR
my-service 
image 
:1.0
:1.1
:2
my-app
image
:5.2
:5.3

Docker hub is a registry 
On docker hub you can host private or public repositories for your applications 
www

Dockerfile - Create own Images 

image 
docker hub
my-app  
Companies create custom images for their application 

Building own Docker Images 

{ JS }
Deploy to server 
We want to deploy our application as a Docker container 
Image 
Run 
Container

Docker - Build instruction 

Build 
Image 
Run
Container 
We need to create a “definition” of how to build an image from our application
Dockerfile 
Dockerfile is a text document that contains commands to assemble an image 
Docker can then build an image by reading those instructions 

Node.js 
We will write a Dockerfile for Node.js application 
Then, build a Docker image from it 

Docker Crash Course for Absolute Beginners
src
js server.js 
{} package.json 
dockerfile

SRC JS server.js 
const express = require (‘express’);
const app = express ();
app.get (‘/’, (req, res) =>{
res.send (“ Welcome to my awesome app!” );
});
app.listen(3000,function () {
console.log (“app listening on port 3000”);
});

package.json 
{
   	“name”: “my-app”,
	“version”:”1.0”,
	“dependencies”:{
	      “express”:”4.18.2”

     }
} 
Terminal 
#[\W (main)]$ node src/server.js

dockerfile 

Dockerfiles start from a parent image or “base image”
It is a Docker image that your image is based on
You choose the base image, depending on which tools you need to have available 

image 
node 
tomcat
python 

Structure of Dockerfile 
FROM 
Dockerfile must begin with a FROM instruction 
Build this image from the specific image 

https://hub.docker.com/_/node
Multi Layer Approach 
 
Image            node                          Image                  my-app
dockerfile       …                              dockerfile             node
node               alpine:3:16                my-app                …
                                                                                     alpine:3:16

Every image consists of multiple image layers

dockerfile 
FROM node:19-alpine

Terminal 
#[\W (main)]$

Structure of dockerfile
FROM
Build this image from the specified image 
RUN 
Will execute any command is a shell inside the container environment 


dockerfile 
FROM node:19-alpine

RUN npm install  

linux operating system
node and npm installed
Copy application file from host into the container 
Executing “npm install”, to install dependencies 
host env 
container env

 
dockerfile 
FROM node:19-alpine

COPY package.json /app/ 
COPY <src> on our machine <dest> in the container 

RUN npm install  

Host 
File system 
Virtual file system of container 

dockerfile 
FROM node:19-alpine

COPY package.json /app/ 
COPY src/app/ 

WORKDIR /app

RUN npm instal

CMD [“node”, “server.js”]

From Dockerfile to Container 
Dockerfile
Build
Image 
Run 
Container 

Build Image 
Dockerfile 
Build 
Image
Now we need to actually build the Docker image from it
  
dockerfile 
FROM node:19-alpine

COPY package.json /app/ 
COPY src/app/ 

WORKDIR /app

RUN npm instal

CMD [“node”, “server.js”]

Terminal 
[\W (main)]$ docker build -t node-app:1.0 . 
docker build {path} = Builds a Docker image from a Dockerfile 
[\W (main)]$

Remember: A Docker image consist of layers 
Each instruction in the Dockerfile creates one layer 
These layers are stacked and each one is a delta of the changes from the previous layer 

[\W (main)]$ docker images
REPOSITORY     TAG               IMAGE ID              CREATED             SIZE 
node-app              1.0                 7b5f1a7948c4       51 seconds ago    182MB
nginx                     1.23               a99a39d070bf       4 days ago            142MB
nginx                     latest              a99a39d070bf       4 days ago            142MB
nginx                    1.22-alpine      c31fe73098ae       2 months ago        23.5MB 
[\W (main)]$ docker run -d -p 3000:3000 node-app:1.0
8e2be3af567f8d8d1996f6f712b76322aee1c254471596caa54740317df511aa
[\W (main)]$ docker ps 
#CONTAINER ID       IMAGE            COMMAND     CREATED      STATUS      PORTS    #NAMES
#8e2be3af567f          node-app:1.0    “/docker-entry…  4 seconds ago Up 4 seconds 0.0.0.0:3000->3000/tcp::3000->3000/tcp  distracted_kare
#a22f17e00535         nginx:1.23   “/docker-entry…3 seconds ago Up 2 seconds #0.0.0.0:9000->80/tcp, :::9000->80tcp web-app
[\W (main)]$
Browser localhost:3000 
Welcome to my awesome app! 
[\W (main)]$ docker logs 8e2be3af567f
app listening on port 3000
[\W (main)]$ 

Dockerrize your own application 
Write Dockerfile 
Build Docker Image
Run as Docker Container 


Using Docker UI Client 

Docker Overview 
Containers/Apps
Images 

Docker in complete software development lifecycle 
Basic building blocks of Docker 
How does Docker fit in and in the complete development and deployment process ? 
 
[
Docker Hub
Developing a JS app
Commit 
Git
Trigger CI/CD 

CI Server 
Builds Docker Image
JavaScript 

Push 
Private Repository 
Pull

Deployment Server 
Both images are pulled on the server 
JavaScript - Image 

Docker hub 
Pull 
]


Developing a JS app 
{;}JS
MongoDB database / docker hub 
Commit 
Git 
Jenkins / Triggers CI/CD / CI server / Builds Docker Image 
Docker Image / JS / Dockerfile 
Push
Private Repository 
Pull
Deployment Server 
Pull
DockerHub
Both images are pulled on the server 


Deployment Server 
Image 
JS
MongoDB 

How Docker is used in a real life development process 

What images are 
How to run containers 
How containers work
How to create your own image 
Basic Docker commands 


