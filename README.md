# Docker Notes [![Generic badge](https://img.shields.io/badge/Sources-1-<COLOR>.svg)]()            [![Generic badge](https://img.shields.io/badge/Notes-206-<COLOR>.svg)]()
## Sources ##
Title  | Link
------------- | -------------
The Ultimate Docker Course  | https://codewithmosh.com/p/the-ultimate-docker-course
## Notes ##
### 1. What is docker? ###
> Docker is a platform for consistently building, running, and shipping applications.
### 2. What do we have problems without docker? ###
> The app works on my machine but doesn't work somewhere.
> 1. One or more files are missing and the app is not entirely deployed
> 2. Software version mismatch
> 3. Different configuration settings
### 3. With docker we can easily ... our application with everything it needs and run it anywhere on any machine with docker. ex? ###
> package
>
> - package 1 : node 14, mongo 4, app
> - package 2: node 13, mongo 3, app
### 4. If someone joins your team, they don't have to spend half of the day setting up a new machine to run the application. 1. What should they do? 2. What does Docker do? ###
> 1. docker-compose up
> 2. docker will automatically download and run this dependency inside an isolated environment called a container.
### 5. After run: docker-compose up, docker will automatically download and run this dependency inside an isolated environment called a ... ###
> container
### 6. ... allows multiple applications to use different versions of some software side by side on the same machine without messing with each other and we can safely remove an application with all dependencies with this command ... ###
> - container(isolated environment)
> - docker-compose down -rmi all
### 7. What's a virtual machine? ex: we have a Mac then we can run ... VMs like ... and ... with What? Defination? The most popular? 3 ###
> A virtual machine is an abstraction of hardware resources.
> - Two
> - Windows & Linux
> - What? hypervisors
> - Definition: Using hypervisors we can create and manage virtual machines.
> - The most popular hypervisors are VirtualBox, VMware and Hyper-v (Windows-only)
### 8. The benefit of VM? 1, The problems of VM? 3 ###
> Run the application in isolation inside a VM.
> - VM 1: node 14, mongo 4, app 1
> - VM 2: node 9, mongo 3, app 2
>
> Problems:
> - Each VM needs a full-blown OS
> - Slow to start
> - Resource intensive
### 9. The benefit of Container 5 ###
> 1. Allow running multiple apps in isolation
> 2. Are lightweight
> 3. Use the OS of the host
> 4. Start quickly
> 5. Need less hardware resource
### 10. Docker uses a ... architecture. It has a ... component that talks to a ... component using a ... The server is also called the .... sits in the background and takes care of building and running docker containers. But technically container is just a ..., like other processes running on your computer. But It's a special kind of process. Unlike VM, containers don't contain a full-blown OS. Instead, all containers on a host share the OS of the host. All containers share the kernel of the host. ###
> - client-server
> - client
> - server
> - RESTful API
> - Docker engine
> - process
### 11. ... ###
### 12. ... ###
### 13. ... ###
### 14. ... ###
### 15. ... ###
### 16. ... ###
### 17. ... ###
### 18. ... ###
### 19. ... ###
### 20. ... ###
### 21. ... ###
### 22. ... ###
