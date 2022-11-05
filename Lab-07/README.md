# Docker Workshop <br/>

Lab 07: Managing Containers <br/>

## Preparations <br/>

* Create a new folder for the lab: <br/>
  $ mkdir lab-07 <br/>
  $ cd lab-07 <br/>

## Instructions <br/>

* Run the following containers using dockerhub images: <br/>

  $ docker run -d -p 5002:5002 -e "port=5002" --name python-app1 selaworkshops/python-app:1.0 <br/>
  $ docker run -d -p 5003:5003 -e "port=5003" --name python-app2 selaworkshops/python-app:2.0 <br/>
  
* Ensure the containers are running: <br/>
  $ docker ps <br/>
  
* Stop the first container:<br/>
  $ docker stop python-app1 

* Kill the second container: <br/>
  $ docker kill python-app2

* Display running containers: <br/>
  $ docker ps
  
* Show all the containers (includind non running containers): <br/>
  $ docker ps -a
  
* Let's start both containers again: <br/>
  $ docker start python-app1 python-app2 

* Restart the second container: <br/>
  $ docker restart python-app2
  
* Display the docker host information with: <br/>
  $ docker info
  
* Show the running processes in the first container using: <br/>
  $ docker top python-app1
  
* Display the resource usage statistics of both containers (exit with Ctrl + C): <br/>
  $ docker stats python-app1 python-app2

* Retrieve the history of the second container image: <br/>
  $ docker history selaworkshops/python-app:2.0 
  
* Inspect the second container image: <br/>
  $ docker inspect selaworkshops/python-app:2.0 
  
* Inspect the first container and look for the internal ip: <br/>
  $ docker inspect python-app1 
 
 "Networks": {<br/>
                "bridge": { <br/>
                    "IPAMConfig": null, <br/>
                    "Links": null,<br/>
                    "Aliases": null, <br/>
                    "NetworkID": "822cb66790c6358d9decab874916120f3bdeff7193a4375c94ca54d50832303d",<br/>
                    "EndpointID": "9aa96dc29be08eddc6d8f429ebecd2285c064fda288681a3611812413cbdfc1f", <br/>
                    "Gateway": "172.17.0.1",<br/>
                    "IPAddress": "172.17.0.3",<br/>
                    "IPPrefixLen": 16,<br/>
                    "IPv6Gateway": "", <br/>
                    "GlobalIPv6Address": "", <br/>
                    "GlobalIPv6PrefixLen": 0, <br/>
                    "MacAddress": "02:42:ac:11:00:03",<br/>
                    "DriverOpts": null<br/>
                }<br/>
            } <br/>
   
   * Show the logs of the second container using the flag --follow: <br/>
     $ docker logs --follow python-app2
     
   * From your browser, browse to the application and watch the containers logs changing in the terminal: <br/>
     http://localhost:5003
     
   * Stop to tracking logs: <br/>
     $ CTRL + C
     
   * Inspect the content of the current directory: <br/>
     $ ls -l
     
   * Copy some files from the second container to the host: <br/>
     $ docker cp python-app2:/app/index.html .
     
   * Inspect the content of the current directory: <br/>
     $ ls -l
     
   * Export the python-app1 container’s filesystem to a tar archive named FS.tar: <br/>
     $ docker export --output="FS.tar" python-app1
   
   
   # Cleanup <br/>
   
   * Remove used containers:
     $ docker rm -f python-app1 python-app2
    
