# docker-crash-course
#### An Image:
 Images are like blue print for containers and they  contained the following inside them :-
 - Runtime enviroment 
 - application code 
 - any dependency
 - extra configurations (Env variables) 
 - commands

NB:- Images are Read only meaning once you created an image it can't not be change, if a change is made a new image needs to be build for that change :
 ### Containers
 This are runable intances of those images. or can they can seen as isolated process. (container are also process).   
  - Containers runs what's outline in the image file.


List of Docker images can be viewd with: `docker images`

### Building an Image
**images are Read only: meaning it can't changes onces it has been build**
````
docker build -t <name of image> <location>
 
// Example: Docker build -t myApp .

````
##### Eunning * Stoping Containers

- ### Running Container  
images are run on containers
````
   // this command creates a new container and run it
docker run --name <container name> <image name >

 every additional flag cames before the image name

example: docker run --name app1_c -p 4000:4000 -d myApp
````
To see  running processes (containers)
```` 
docker ps  
docker ps -a // list all containers
```` 
- Docker containers can also be run specifying their name, port number if it was expose in the docker config file.

    For example: 
    ```` 
    docker run --name <containerName> -p <define port in local machine>:<port in container>
  -d <name o image>.   

    docker run --name <containerName> -p 4000:4000 -d my App 
    ````

- ### Starting Container  

```
docker start <nameOf container> 
docker stop <nameOf container> -f // to forcely closed it even it's running

```
### Layer caching in Docker

- improving caching can be done by copying the package.json before copying the source code into the working dir

```
COPY package.json . 
```

### Deleting Containers and Images
- Deleting Containers:
````
// deleting containers
  docker container rm name/id of container

//deleting images
  docker image rm name/id of image

// deleting more than one container
  docker container rm name/id of container 1  container 2 container 3 .......

// deleting more than one image
  docker image rm name/id of image 1  image 2 image 3 .......
  ````
### Delete All Containers and Images in the SYSTEM 
````
docker system prune -a  // take caution
````
#### Specifying image version
```` 
docker build -t node-app:v1 .    // node-app could have many versions
````

## Docker Composer 
THe docker composer file defines the configuration for all the services (images) in a project.
````
dokcer-compose runs the docker composer file with all the services inside