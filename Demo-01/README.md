# **Docker Workshop**<br/>
Demo 01: First touch with containers
# **Preparations** <br/>
* Pull Jenkins image with below command.<br/>

  $ docker pull jenkins/jenkins

# **Instructions** <br/>
* Check the current running containers and images: <br/>
  $ docker ps <br/>
  $ docker images <br/>

* Browse to the port 8080 to show to show that it's empty: </br>
  http://localhost:8080/
  
* Run a Jenkins container
  $ docker run --name jenkins -p 8080:8080 jenkins/jenkins
* Browse to the Jenkins application <br/>
* http://localhost:8080/

* Look up the administrator password in the log in your screen/terminal:

![image](https://user-images.githubusercontent.com/117446926/199962094-bb916349-358f-4f3e-be84-4bb600830015.png)

* Configure Jenkins using the administration password
* Exit and stop the container by using "Ctrl + C"
* Remove the stopped container <br/>
  $ docker rm -f jenkins
