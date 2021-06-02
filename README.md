# Basics-of-Docker
Learn Basic Commands for Docker.

## Docker
- A platform for running, building, and shipping applications. 
- Build, Run and Ship the application.

## Container
- A container is an Isolated Environment for running an Application.

## Q. How are Containers different from Virtual Machines?

- A virtual machine is an abstraction of a  machine(physical hardware).
  E.g On a windows machine, we can run two virtual machines, viz Mac and Ubuntu, using a Hypervisor tool.
  There are many Hypervisors available like Vmware, Virtual Box, etc.

### Problems with Virtual Machine:
  -  Each VM needs a full-blown OS
  -  Slow to start
  -  Resource intensive
  	
###	Benefits of Containers:
- Allow running multiple apps in isolation
- Are lightweight
- Use the OS of the host.
- Start quickly
- Need fewer hardware resources.

### Key differences:
- Size: Docker images are much smaller, while VM images may in few gigabytes.
- Speed: Docker Containers start and run fast.

## Architecture of Docker
- Docker uses Client-Server architecture. So it has a client component that talks to a Server component using a RESTful API. This server is also called Docker Engine, sets in the background and takes cares of building and running Docker containers.
- Technically a Container is just a process like another process running on your computer. It is a special kind of process.
- All these containers share the kernel of the host. The kernel is the core of the operating system. It is just like the engine of a car.
  A kernel manages applications and hardware resources.
  
### Before Containers:
- Configuration on the server needed.
- Dependency version conflicts.
- Misunderstanding between Development teams & operating teams.
- Textual guide of Instructions.

## Main Docker Commands

<p> For public repository, you don’t need to log in, Authentication.

Installation of some public repository.
E.g postgres
</p>

<p>
Steps:
Visit hub.docker.com and search for any public repo.
E.g postgres
</p>

### Installation commands ###
`docker pull postgres`
  - this will pull the image and install the latest version from the repo.
  
`docker run postgres`
  - this will first if the image is already in local machine and if not available it will install it from the docker hub, also it going execute start scripts as soon as you download it.

### Installation of Specific version
`docker run postgres:9.6`

### Note: 
- Docker Containers are made of layers you have Linux Image Layer, Application Layer, and so on.
- Whenever we try to install 

<p> The application of separation images is, suppose the newer version of postgres is released, then I don’t need to download the same layers again on my machine, only different layers are downloaded. </p>

- Output: After downloading it also execute the scripts.


### Command: `docker ps`
- It will show us all running containers i.e it shows image postgres:9.6 is running.



## Docker Image vs Docker Container

> Docker Image
- It is actual package e.g Postgres
- artifact, that can be move around.

> Docker Container
- actually starts the application.
- container environment is created.
- container is running environment for image.
- virtual file system.

## Main Docker Commands

`docker pull redis`
- It will pull image from docker hub

`docker images`
- It will check all existing images on our machine.
- TAG is basically a version of the image.
- This is just an image and the container is not running till now.

`docker run redis`
- it pulls the image and starts the container.
- this will actually start an image in a container.
- Now we need to create a container to connect to the Redis application.
- container is the running environment for the image.

`docker ps`
- It lists all running docker containers.


`docker run -d redis`
- Get id of the container.
- if you again run docker ps, you will get same id.


`docker stop ‘container_id’`
- E.g docker stop 52199d8f42a4
- If you run again ‘docker ps’


`docker start ‘container_id’`
- It will start the stopped container.
- E.g docker start 52199d8f42a4


`docker ps -a`
- Suppose we stopped the container and want to know which container I have started earlier, we can use the above command.
- It lists all running and stopped containers.



`docker run redis:5.0`
- Installs a specific version of the image as per requirement.
- Suppose you need to use a tool with different versions of Redis.
- So we will need two containers of redis with a different version of images.

`Delete a Specific Container`
- It removes a specific container from the machine.
- docker container rm b6424cc6fb32


## Q. How to avoid port conflict in multiple Docker Containers?

 - It is absolutely fine for HOST to run Container on the same port until and unless we have done its **PORT Binding**.
 - In the below example, we have the 2nd and 3rd Container both listening on port **3000** which is absolutely Ok as long as you bind to two different ports from your host machine.
 - So the port binding between host and container is already done, you can actually connect to the running container using the port of the host. 
 
 - Binding the Ports 
→ Steps: 
	   - 1. Stop running images. ( docker stop ‘id’)
     
     - 2.  Binding it two different ports using ‘run’ commands.
            E.g `docker run -p 6000:6379 redis`
            <p> 6000- port of the host
                6979- port of the container </p>
                
     - 3. Binding Check
          `docker ps`
          
     - 4. Stop all running docker
	        `docker stop id`
     
     - 4. Running container in detached mode.
          `docker run -p 6000:6379 -d redis`
          `docker run -p 6001:6379 -d redis:5.0`
             

## Debugging Containers

`docker logs`
`docker exec -it`

### Q. Check what is the log generated by Redis?
   
```
    docker ps
    docker logs ‘contianer_id’ or docker logs
    e.g `docker logs 993t22rh32h2
```
   
  ### Using name: 
  `docker logs old_image`
  
 
 ## Creating Replica of Container

- If Container is already, stop it first using `docker stop id`

### Creating Replica
- Specify a new name to an existing image, this will create another image that can be helpful for debugging.

### Execute Command for Docker
- This can be helpful when there is a complex configuration.
- Using `docker exec -it`, we can get the terminal of the running container and also root access of container.
- Suppose one of the images is having a problem in the container and we need to debug it.
→ `docker exec -it container_id bin/bash`


  


          





 
 
 
 


 



