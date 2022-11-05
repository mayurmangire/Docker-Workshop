# Docker Workshop <br/>
Lab 04: Updating and Sharing Containers

# Preparations
* Create a new folder for the lab:
  $ mkdir lab-04
  $ cd lab-04
  
# Docker Commit
* Run the application (version 3.0) in a Docker container (detached mode) in the port 5000 using:<br/>
  $ docker run -d -p 5000:3000 --name static-app-3.0 selaworkshops/npm-static-app:3.0
* Ensure the container is running: <br/>
  $ docker ps
* Open a Bash terminal in the container using the exec command: <br/>
  $ docker exec -it static-app-3.0 /bin/bash
* Create a new file in the container using this command:<br/>
$- echo "Very secret content :)" > secret-file <br/>
$- # ls -l <br/>
     cat secret-file <br/>
     exit </br>
* Check the current images:
  $ docker images
* Create a new image including the changes: <br/>
  $ docker commit static-app-3.0 selaworkshops/npm-static-app:3.1
* Check the current images: <br/>
  $ docker images
* Delete the container static-app-3.0 using: <br/>
  $ docker rm -f static-app-3.0
* Run a new container from the version 3.0 image (in port 5000): <br/>
  $ docker run -d -p 5000:3000 --name static-app-3.0 selaworkshops/npm-static-app:3.0
* Run a container from the newly created 3.1 image (in port 5001): <br />
  $ docker run -d -p 5001:3000 --name static-app-3.1 selaworkshops/npm-static-app:3.1
* Inspect the running containers with:<br/>
  $ docker ps
* Inspect the filesystem of the version 3.0 container:<br/>
  $ docker exec static-app-3.0 ls -l
* Inspect the filesystem of the commited 3.1 container: <br/>
  $ docker exec static-app-3.1 ls -l
* We see images doesn't change when a container changes but you can "commit" new images to save the container changes <br/>

# Docker Save <br/>
* Now let's save the commited container in a file (and store it in the current directory):<br/>
$ docker save -o static-app-3.1.tar selaworkshops/npm-static-app:3.1
* Ensure the image was created in the current directory: <br/>
$ ls

# Docker Load <br/>
* Clean your docker host environment: <br/>
$ docker rm -f $(docker ps -a -q)
$ docker rmi -f $(docker images -a -q)
* Ensure that your Docker engine's environment is clean:<br/>
$ docker ps -a <br/>
$ docker images <br/>
* Let's load the Docker image from the created file: <br/>
$ docker load -i static-app-3.1.tar
* Ensure the image was loaded successfully: <br/>
$ docker images
* Clean your Docker engine's environment: <br/>
$ docker rmi -f $(docker images -a -q)

