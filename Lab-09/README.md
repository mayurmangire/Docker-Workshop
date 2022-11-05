# Docker Workshop <br/>
  Lab 09: Docker Networks 
  
## Instructions <br/>

* Display all existing networks on the host: <br/>
  $ docker network ls
  
* Let's create a new bridge type network: <br/>
  $ docker network create -d bridge my-bridge-network
  
* Run the app container linked to the created network: <br/>
  $ docker run -d -p 8081:8081 -e "port=8081" --name app --network=my-bridge-network selaworkshops/python-app:2.0 <br/>
  
* Find the container internal ip using the command: <br/>
  $ docker inspect app <br/>
  ![image](https://user-images.githubusercontent.com/92582005/200118120-326a60ed-9481-4d4d-9b86-285b5622f0a8.png) <br/>
  
* Open a new terminal and run an ubuntu container in interactive mode: <br/>
  $ docker run -it --name ubuntu selaworkshops/ubuntu:18.04
  
* Install curl on the ubuntu container: <br/>
  $ apt-get update
  $ apt-get install curl -y

* From the ubuntu's container terminal try to browse to the app container: <br/>
  $ curl <app-container-internal-ip>:8081

* **It is not working..** <br/>
* From the other terminal session (host terminal) run the command below to attach the ubuntu container to the created network: <br/>
  $ docker network connect my-bridge-network ubuntu
 
* From the ubuntu container terminal try to browse to the app container again: <br/>
  $ curl <app-container-internal-ip>:8081
* Now you will be able to reach the application: <br/>
  <h1>Python App</h1>
  
* Inspect the network from the host terminal and look for the linked containers: <br/>
  $ docker inspect my-bridge-network <br/>
  ![image](https://user-images.githubusercontent.com/92582005/200118569-32befe8c-013d-4086-839d-a2126200eb79.png) <br/>
  
* Disconnect both containers from the created network (regular terminal): <br/>
  $ docker network disconnect my-bridge-network app <br/>
  $ docker network disconnect my-bridge-network ubuntu <br/>
  
* Exit from the ubuntu container and close the terminal: <br/>
  $ exit
  
# Round Robin networking <br/>

* Create a new container named web-server-1 with a network alias web-service <br/>
  $ docker run -it -d --network-alias web-service --network=my-bridge-network --name web-server-1 selaworkshops/ubuntu:18.04 <br/>
* Create a new container named web-server-2 with a network alias web-service <br/>
  $ docker run -it -d --network-alias web-service --network=my-bridge-network --name web-server-2 selaworkshops/ubuntu:18.04 <br/>
* Create a new container named DNS-looker that will run with the nslookup command that which in turn shows us all the containers under the web-service DNS name.<br/>
  $ docker run -it --network=my-bridge-network --name DNS-looker  selaworkshops/alpine_new:3.4 nslookup web-service <br/>
  ![image](https://user-images.githubusercontent.com/92582005/200119033-31a45924-f6bb-462a-8716-628bb1a43301.png) <br/> <br/>
  
* As it can be seen that there are two containers under the same name, that is how you form a round robin effectively <br/>

# Cleanup <br/>

* Remove used containers: <br/>
  $ docker rm -f app ubuntu web-server-1 web-server-2  DNS-looker <br/>
  
* Delete the network: <br/>
$ docker network rm my-bridge-network <br/>

* Ensure that the network was deleted: <br/>
  $ docker network ls
  

  

