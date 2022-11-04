# Docker Workshop <br/>
Lab 03: Running commands inside the container

## Instructions <br/>
* Run the application in a Docker container (detached mode) using: <br/>
  $ docker run -d -p 3000:3000 --name app selaworkshops/npm-static-app:latest
* Ensure the container is running: <br/>
  $ docker ps
* Attach to the container process using: <br/>
  $ docker attach app <br/>
* Note that you are attached to the server process, not to a terminal inside the container
* You are not stuck, this is fine
* Exit from the process by clicking on the command below couple of times:<br/>
  $ (CTRL + C)
* Check the status running containers: <br/>
  $ docker ps
* Show the stopped containers as well: <br/>
  $ docker ps -a
* Execute the terminal (interactive) inside the container using:<br/>
  $ docker exec -it app /bin/bash
* Inspect the container's filesystem: ("#" sign here indicates that you are inside the container) <br/>
** ls -l <br/>
** pwd <br/>
** cd / <br/>
** ls -l <br/>


* Exit from the container terminal using: <br/>
  $ exit
* Check the running containers: <br/>
  $ docker ps
* Remove the "app" container: <br/>
  $ docker rm -f app
