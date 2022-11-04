# Docker Workshop <br/>
Lab 02: Basic commands

## Notes
* During the lab we will use the following image which is a simple web application. <br/>
    https://hub.docker.com/r/selaworkshops/npm-static-app/
## Instructions

* Create a new container from the image without running it: <br/>
  $ docker create --name app-stopped selaworkshops/npm-static-app:latest <br/>
* Create and run a new container (in detached mode) using: <br/>
  $ docker run -d -p 3000:3000 --name app-running selaworkshops/npm-static-app:latest
* Check that the second container is up and running:
  $ docker ps
* Check that the first container was created but is not running: <br/>
  $ docker ps -a
* Via your browser browse to the running container application at port 3000:<br/>
  $ http://localhost:3000
* Check which images exist in your host: <br/>
  $ docker images
* Remove both containers (with the force flag): <br/>
  $ docker rm -f app-running app-stopped
* Check Via browser if the website is still operational: <br/>
  $ http://localhost:3000
* Remove the container's image: <br/>
  $ docker rmi selaworkshops/npm-static-app:latest
* Check the containers status: <br/> 
  $ docker ps -a
* Check the images status: <br/>
  $ docker images

