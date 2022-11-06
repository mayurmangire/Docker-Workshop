# Docker Workshop <br/>
Lab 01: Installing Docker in Ubuntu <br/>

* Update the apt package index: <br/>
  $ sudo apt-get update <br/>
  
* Install packages to allow apt to use a repository over HTTPS:
  $ sudo apt-get -y install apt-transport-https ca-certificates curl software-properties-common

* Add Docker’s official GPG key: <br/>
  $ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
  
* Use the following command to set up the stable repository: <br/>
  $ sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" <br/>
  
* Update the apt package index: <br/>
  $ sudo apt-get update <br/>
  
* Install the latest version of Docker CE: <br/>
  $ sudo apt-get -y install docker-ce <br/>
  
* Start the Docker daemon: <br/>
  $ sudo service docker start <br/>
 
* Create the docker group (if it doesn't exist): <br/>
  $ sudo groupadd docker
  
* Add your user to the docker group (to be able to run docker without sudo): <br/>
  $ sudo usermod -aG docker $USER 
  
* Close & open a new terminal session :

* Verify that you can run the following commands without sudo:<br/>
  $ docker run hello-world <br/>
  $ docker ps -a <br/>

### Official Docker Links : <br/>

* Install Docker : <br/>

   https://docs.docker.com/engine/install/ <br/>
  
* Post-installation steps for Linux <br/>

  https://docs.docker.com/engine/install/linux-postinstall/
