# Docker Workshop <br/>
Demo 02: Understanding the Docker Components

## Instructions 
* Access to the grafana repository: <br/>
  https://hub.docker.com/r/grafana/grafana
* Show the repository image tags: <br/>
  https://hub.docker.com/r/grafana/grafana/tags/
* Go to the terminal and check the existent images using: <br/>
  $ docker images <br/>
* Pull the version 6.2.5 with:<br/>
  $ docker pull grafana/grafana:6.2.5
* Show the existent images and look for the pulled image:<br/>
  $ docker images
* Show the current running containers using:<br/>
  $ docker ps
* Create a new container from the pulled image: <br/>
  $ docker run -d -p 3000:3000 --name grafana grafana/grafana:6.2.5
* Check if the new container is running now: <br/>
  $ docker ps
* Browse to the application:<br/>
  http://localhost:3000/
* Clean up <br/>
  $ docker rm -f grafana
