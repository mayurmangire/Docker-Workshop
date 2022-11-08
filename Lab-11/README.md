## Docker Workshop <br/>
Lab 11: Docker Compose <br/>

## Install docker-compose <br/>
* install docker-compose: <br/>
  $ sudo apt install docker-compose <br/>
  
## Preparations <br/>

* The docker-compose file referred in the lab is available for download. 
* Create a new folder for the lab: <br/>
  mkdir lab-11 <br/>
  cd lab-11 <br/>
  
## Instructions <br/>

* Create a "docker-compose.yml" file with the content below: <br/>
  ![image](https://user-images.githubusercontent.com/92582005/200121525-8b3dfd7d-893e-4d13-93a0-da768a09c421.png) <br/>
  
* Start all the environment in detached mode: <br/>
  $ docker-compose up -d
  
* Wait until docker complete to start the containers, meanwhile let's inspect the wordpress logs: <br/>
  $ docker-compose logs -f wordpress <br/>
  
* Check the running containers: <br/>
  docker-compose ps <br/>
  
* Browse to the wordpress portal: <br/>
  http://localhost:8000 <br/>
  
* Enter to the mysql container: <br/>
  $ docker-compose exec db bin/bash <br/>
  
* Print the environment variable "MYSQL_USER" (passed in the yaml file): <br/>
  $ echo $MYSQL_USER <br/>
  
* Exit from the container <br/>
  $ exit <br/>

* Update the mysql image used in the docker-compose.yml file to "5.7.24": <br/>
  
  ![image](https://user-images.githubusercontent.com/92582005/200121845-7dc9cfb2-2bdf-4ec9-a03d-aec2eb9563fe.png) <br/>
  
* Apply the changes to the running environment: <br/>
  $ docker-compose up -d <br/>

* Let's clean our environment (remove the containers defined in the docker-compose file): <br/>
  $ docker-compose down <br/>
  
* Note that volumes are not deleted by default, so you can recreate the environment at any time <br/>
  $ docker volume ls <br/>
  
* To remove the volumes as well you can use "docker-compose down --volume"
  

 
  

