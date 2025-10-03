# Creating a docker and container 

## Creating the docker image
docker pull image_name

docker pull ubuntu

## Creating the container
docker run -it ubuntu

## Building the docker 
docker build -t path-to-docker-file

docker build -t demo-docker .

## To Display the docker images 
docker images

## To run the images
docker run image-name

docker run demo-docker

## To open SH in your docker image 
docker run -it demo-docker sh 

## To map port on host machine to docker 
docker run -p 5173:5173 react-docker

## To mount or link the local directory to the container directory (app)
docker run -p 5173:5173  -v "$(pwd):/app" -v /app/node_modules react-docker

## To get list of docker images 
docker ps

## To get all  the docker images
docker ps -a

## To remove all the container 
docker container prune 