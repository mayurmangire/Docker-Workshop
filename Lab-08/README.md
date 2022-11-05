# Docker Workshop <br/>
Lab 08: Using Volumes <br/>

### Instructions <br/>

* Display existent volumes: <br/>
  $ docker volume ls
  
* Create a new volume: <br/>
  $ docker volume create my-volume
  
* Inspect the new volume to find the mountpoint (volume location): <br/>
  $ docker volume inspect my-volume <br/>
  
  ![image](https://user-images.githubusercontent.com/117446926/200117194-bdd1a419-0536-47a2-9427-b8af1043e032.png) <br/>
  
* Please run a container and mount the created volume to the /data folder inside the container: <br/>
  $ docker run -it -v my-volume:/data --name my-container selaworkshops/busybox:latest
  
* Now you are inside the container, please create a new file under /data: <br/>
  $ cd /data <br/>
  $ touch new-file <br/>
  $ ls <br/>

* Open another terminal and run another container with the same volume mapping: <br/>
  $ docker run -it -v my-volume:/data --name my-container-2 selaworkshops/busybox:latest
  
* Now you are inside my-container-2, Inspect the /data folder (the created file will be there): <br/>
  $ cd /data <br/>
  $ ls <br/>
 
* Exit from both containers and delete them: <br/>
  $ exit <br/>
  $ docker rm -f my-container my-container-2 <br/>
  
* Ensure the containers were deleted <br/>
  $ docker ps -a
 
* Run a new container while attaching the previously created volume: <br/>
  $ docker run -it -v my-volume:/data --name new-container selaworkshops/busybox:latest

* Inspect the /data folder inside the new-container (the created file will be there): <br/>
  $ cd /data <br/>
  $ ls <br/>
  
* Exit from the container and delete it: <br/>
  $ exit <br/>
  $ docker rm -f new-container <br/>

* Remove the created volume: <br/>
  $ docker volume rm my-volume <br/>
  
* Display existent volumes: <br/>
  $ docker volume ls
  

  
