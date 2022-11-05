# Docker Workshop <br/>
Lab 06: Building more complex images

# Instructions <br/>
* Ensure you are in the previous created folder path (lab-05):<br/>
$ pwd
* Create a file named "index.html" next to the Dockerfile with the content below: <br/> 
  echo "<h1>Python App</h1>" > index.html
* Check your current directory before you proceed: <br/>
  $ ls -l <br/>

  total 2 <br/>
  -rw-r--r-- 1 docker 1049089 123 Jun 13 21:37 Dockerfile <br/>
  -rw-r--r-- 1 docker 1049089  19 Jun 13 21:54 index.html <br/>

* Edit the Dockerfile to expose the port 5000 <br/>
  EXPOSE 5000
* Like as below: <br/>
  FROM selaworkshops/alpine_new:3.4 <br/>
  RUN apk add --no-cache python <br/>
  CMD python -m SimpleHTTPServer 5000 <br/>
  EXPOSE 5000 <br/>

* Replace the CMD instruction for ENTRYPOINT to avoid override the command from the docker run command: <br/>
  ENTRYPOINT python -m SimpleHTTPServer 5000
* Like below <br/> <br/>
  FROM selaworkshops/alpine_new:3.4 <br/>
  RUN apk add --no-cache python <br/>
  ENTRYPOINT python -m SimpleHTTPServer 5000 <br/>
  EXPOSE 5000 <br/><br/>
  
* Add a build argument to set the application port during the build: <br/> 
  ARG port=5000 <br/>
  EXPOSE $port <br/>
  
* Like below : <br/>
  FROM selaworkshops/alpine_new:3.4 <br/>
  RUN apk add --no-cache python <br/>
  ARG port=5000 <br/>
  ENTRYPOINT python -m SimpleHTTPServer $port <br/>
  EXPOSE $port <br/>
  
* Add a environment variable to override the build argument at runtime: <br/>
  ENV port=$port

* Like Below.<br/>

  FROM selaworkshops/alpine_new:3.4 <br/>
  RUN apk add --no-cache python <br/>
  ARG port=5000 <br/>
  ENV port=$port <br/>
  ENTRYPOINT python -m SimpleHTTPServer $port <br/>
  EXPOSE $port <br/>
  
* Set the app directory as the container working directory:<br/>

  WORKDIR /app <br/>
  
* Like below <br/>
  FROM selaworkshops/alpine_new:3.4 <br/>
  RUN apk add --no-cache python <br/>
  ARG port=5000 <br/>
  ENV port=$port <br/>
  WORKDIR /app <br/>
  ENTRYPOINT python -m SimpleHTTPServer $port <br/>
  EXPOSE $port <br/>
 
 * Copy the index file to the container using the COPY instruction: <br/>
   COPY index.html /app/ <br/>
   
 *  Like below <br/>
    FROM selaworkshops/alpine_new:3.4 <br/>
    RUN apk add --no-cache python <br/>
    ARG port=5000 <br/>
    ENV port=$port <br/>
    WORKDIR /app <br/>
    COPY index.html /app/ <br/>
    ENTRYPOINT python -m SimpleHTTPServer $port <br/>
    EXPOSE $port <br/>
    
 * Build the new image passing a build argument: <br/>
   $ docker build --build-arg port=5001 -t python-app:2.0 . <br/>
 
 * Run the created image without passing environment variables: <br/>
   $ docker run -it --name app1 -p 5001:5001 python-app:2.0 <br/>
 
 * Browse to the application: <br/>
   http://localhost:5001  <br/>
   
 * Exit from the running container: <br/>
   $ (Ctrl + C) <br/>
   
 * Run the created image passing the port 5002 as parameter: <br/>
   $ docker run -it --name app2 -p 5002:5002 -e "port=5002" python-app:2.0 <br/>
   
 * Browse to the application: <br/>
   http://localhost:5002 <br/>
  
 * Exit from the running container: <br/>
   $ (Ctrl + C) <br/>
   
 # Clean up <br/>
 
 * Remove used containers: <br/>
   $ docker rm -f app1 app2




  





