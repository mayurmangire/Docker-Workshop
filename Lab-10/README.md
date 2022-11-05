# Docker Workshop <br/>
Lab 10: Working with Docker Hub (Registry) <br/>

## Preparations <br/>

* Create a new folder for the lab: <br/>
  $ mkdir lab-10 <br/>
  $ cd lab-10
  
## Instructions <br/>

* Browse to docker hub and sign up:<br/>
  https://hub.docker.com
  
* Create a new repository called "voting-app": <br/>
  https://hub.docker.com/add/repository/
  
* Create a index.html file with the content below: <br/>
  
     ![image](https://user-images.githubusercontent.com/92582005/200120030-18f2937a-62f9-41b0-923f-c4b2026ee5fd.png) <br/>
     
* Create a Dockerfile with the content below: <br/>
  FROM selaworkshops/ngnix:alpine
  COPY index.html /usr/share/nginx/html
  
* Build the docker image: <br/>
  $ docker build -t voting-app:latest .

* Run the application to ensure that everything it's ok: <br/>
  $  docker run -d -p 8082:80 --name voting-app voting-app:latest
  
* Browse to the application page: <br/>
  http://localhost:8082
  
* Remove the created container: <br/>
  $ docker rm -f voting-app
  
* Let's create two tags for the image we want to push to docker hub: <br/>
  $ docker tag voting-app:latest <your-dockerhub-username>/voting-app:1.0
  $ docker tag voting-app:latest <your-dockerhub-username>/voting-app:latest
  
* Login to docker hub from the terminal: <br/>
  $ docker login
    Login with your Docker ID to push and pull images from Docker Hub. If you don't have a Docker ID, head over to https://hub.docker.com to create one.<br/>
    Username: (your-dockerhub-username) <br/>
    Password: (your-dockerhub-password) <br/>
  
 * Push the images to docker hub: <br/> 
   $ docker push <your-dockerhub-username>/voting-app:1.0 <br/>
   $ docker push <your-dockerhub-username>/voting-app:latest  <br/>
  
* See the pushed images in the docker hub page : <br/>
  https://hub.docker.com/r/(your-dockerhub-username)/voting-app/tags/  <br/>



