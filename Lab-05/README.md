# Docker Workshop <br/>
Lab 05: Building your first image

# Preparations <br/>
* Create a new folder for the lab:<br/>
$ mkdir lab-05
$ cd lab-05

# Instructions <br/>
* Create a new file called "Dockerfile" with the following content:<br/>
FROM selaworkshops/alpine_new:3.4 <br/>
RUN apk add --no-cache python <br/>
CMD python -m SimpleHTTPServer 5000 <br/>

* Build the image using the command: <br/>
  $ docker build -t python-app:1.0 .
* Ensure the image was created:<br/>
$ docker images 
* Run the created image in interactive mode to attach to the container process:<br/>
$ docker run -it --name pythonlab3 python-app:1.0 
* Browse to the port 5000 to check if you can reach the application: <br/>
 http://localhost:5000 <br/>
* It is not working, That is fine!<br/>
* Port 5000 is not exposed to the host therefore we can not reach the application. We will see how to expose the container's ports in the next module.<br/>
* Exit from the container using: <br/>
$ CTRL + C 
* Now, Docker run the same image but pass a command as "run parameters": <br/>
$ docker run -it python-app:1.0 "echo" "Proof of override command!"
* As you may have noticed the command inside the container was overridden by the command passed as parameter in the docker run command
