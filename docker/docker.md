monolith vs microservice

container engine
- docker
- container-D
- CRI-O
- Rocket


docker(container engine) vs kubernets cluster(container orchestration)
1 ec2 - docker              |           3 ec2 - kubernets 
docker swarn                |           container-D / orcherstration


Docker HUB (container registry)
1. hub.docker.com
2. ec2 
    ```
    apt update -y
    curl https://get.docker.com/ | bash
    docker login -u <username>
    ```

```
docker run -d --name <app-name> nginx // pulled image from dockerhub, -d = detached, 
docker exec -it web1 bash // to go inside containe and by default its in running state, -it = iterative
exit // to stop the container
docker start <app-name> 
docker ps
docker ps -a // running and stopped
docker ps -q // return all container ids
docker ps -aq // return all the container ids

docker stop $(docker ps -q)
docker start $(docker ps -aq)

docker rm <container-id>
docker rm $(docker ps -aq)

docker network ls

docker run -d --name <app-name> --publish <app-port>:<server-port> nginx // port farwording condition

docker run -d --name web1 --publish 7000:80 nginx

//DOCKER COMMIT METHOD
create reposity in dockerhub
docker commit <container-id> <repository-name>:<tag-name>
docker images
docker push <repository-name>:<tag-name>
docker rmi <docker-image>

docker inspect web1
```

--------------------------


server      >       ec2 (vm)    >    Docker

PHYSCIAL    >       Virtual     >    Images



NETWORK INTERFACE CARD / NIC 

container   container container

docker0 (bridge)

ethc/wifi0

---

AWS
EC2 -> Configure/install ->AMI

Docker(image)
- Commit
Container -> Configure -> image

- build
docker file


-----

DOCKER FILE METHID

FROM nginx:latest
COPY index.html /usr/share/nginx/html/index.html
EXPOSE 80
CMD ["nginx","-g","dameon off;"] // daemon means process, java daemon, etc

vi Dockerfile
docker build -t  dockhubrepo:imagename 

docker commit <container-id> <repository-name>:<tag-name>


FROM nginx:latest
RUN mkdir /opt/tomcat
WORKDIR /opt/tomcat
COPY . .
EXPOSE 80
// docker run -it --name web1 repo:iamge /bin/bash

// what is dangling images ? 
docker prune -a  // deletes all dangling images



// docker volumnes reference videos

// Interview question 
1. docker network
2. docker file
3. dangling images
4. build
5. commit
6. image size is large // ans: multi stage layers
7. image scaning // ans: synk tool
