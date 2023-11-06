# Docker Notes [![Generic badge](https://img.shields.io/badge/Sources-1-<COLOR>.svg)]()            [![Generic badge](https://img.shields.io/badge/Notes-206-<COLOR>.svg)]()
## Sources ##
Title  | Link
------------- | -------------
The Ultimate Docker Course  | https://codewithmosh.com/p/the-ultimate-docker-course
## Notes ##
### 1. What is docker? ###
> Docker is a platform for consistently building, running, and shipping applications.
### 2. What problems do we have without docker? ###
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
### 11. What's the kernel? Every OS has its own ... or ... and these kernels have different ... That's why we cannot run a Windows application on Linux. ###
> - The kernel is the core of an OS. It's like the engine of a car. It's the part that manages all applications as well as hardware resources like memory and CPU.
> - kernel or engine
> - APIs.
### 12. run containers? Windows = ? Linux = ? Mac = ? ###
> - Windows = Windows(share the windows kernel) + Linux(share the Linux kernel)
because win10 is now shipped with a custom-built Linux kernel.
> - Linux = only Linux containers
> - Mac = doesn't have native support for containerized apps, use a lightweight Linux virtual VM to run Linux containers.
### 13. Docker version? How can find it's correct? ###
> - docker version
> - client and server show information
### 14. for Dockerize we need to add a... file to project. ###
> - dockerfile
### 15. it's a doc plain text file that includes instructions that docker uses to package up the application? into an ... ###
> - dockerfile
> - image
### 16. contains everything our app needs to run. ex? 5 ###
> - image
> - a cut-down OS
> - a runtime env (Node)
> - App files
> - Third-party library
> - Env variables
### 17. we have an ..., we tell docker to start a ... using that ... <br> ... is just a process, but it's a special kind of process because it has its own ... which is provided by the ... and our app gets loaded inside the ... or ... and this is how we run our app locally or in production ###
> - image
> - container
> - image
> - container
> - file system
> - image
> - container or process
### 18. instead of directly running the app on our development machine we tell ... to run it inside ... an isolated environment. ###
> - Docker
> - container
### 19. we have an image. we can push it to a ... register like ... and anyone can use it. it's like ... for git. Then we can put it on any machine(TEST/PROD) ###
> - Docker
> - Docker hub
> - github
### 20. with docker, we no longer need to maintain long complex releases ... that have to be precisely followed. All the instructions for building an image of an app are written in a ... ###
> - Documents
> - Dockerfile
### 21. name of docker file and extension? ###
> - Dockerfile
> - not extension
### 22. Refactor <br> FROM node:alpine <br> COPY . /app <br> CMD node /app/app.js ###
> - FROM node:alpine
> - COPY . /app
> - WORKDIR /app
> - CMD node app.js
### 23. build an image hello-docker 3 ###
> - docker build -t hello-docker .
> - docker buildx build -t hello-docker .
> - docker image build -t hello-world .
### 24. show list of images ###
> docker image ls
### 25. why in this command <br> Docker image <br> show the name of the image below the column called "repository" ###
> because an image is like a repository in GitHub but actually it's on the docker hub.
### 26. How run an image ###
> docker run hello-docker
### 27. How can play with docker online? website? ###
> https://labs.play-with-docker.com/
### 28. how to pull an image ###
> docker pull mosh/hello-docker
### 29. How to push an image? 2 ###
> - docker tag local-image:tagname userName/imageName:tag
> - docker push userName/imageName:tag
### 30. Docker is built on basic ... concept. ###
> Linux
### 31. Linux distributions called ... (5) ###
> - distros
> - Ubuntu / Debian / Alpine / Fedora / CentOS
### 32. How to pull an image?(2) difference? ###
> - docker pull ubuntu // just pull
> - docker run ubuntu <br>
if you have this image locally, Doker is going to start a cotainer with this image. Otherwise, it's going to pull the image behind the scene, and then start a container.
### 33. docker run ubuntu <br> what happens after this command? solution? ###
> Docker has started a container. But because we didn't interact with the container, the container stopped.
> - docker run -it ubuntu
### 34. see the list of running processes or running containers? (2) ###
> - docker ps // show running
> - docker ps -a // show all
### 35. A ... is a program that takes our commands and passes them to the operating system for execution. ###
> shell
### 36. What's this? what does each part mean? <br> root@123:/# ###
> - shell prompt
> - root: currently logged user, by default we logged by the root user with the highest privileges.
> - 123: name of the machine, ID of the container that automatically generates by docker.
> - /: forward slash, where we are in the file system. / represents the root directory. the highest directory in the filesystem.
> - #: number sign | pond sign | show I have the highest privileges = root user, $ means normal user
### 37. We have a program called bash, which is short for .... So apparently, Steve Bourne is the first person who created a shell program, bash, or warning, and the shell is a reference to Steve Borne. So Bash is an enhanced version of the original shell program. ###
> Bourne again shell
### 38. cmd: Print a text in the command line ###
> echo hello
### 39. cmd: Show the current user ###
> whoami
### 40. cmd: Location of shell program ###
> echo $0 // /bin/bash
### 41. separate file & directory in Windows and linux ###
> - linux = / forward slash
> - windows = \ back slash
### 42. Linux is case-sensitive (t/f) ###
> - t
> - check the name of the file & dir & cmd are correct!
### 43. show history of executed command? 2 ###
> - history
> - !2
### 44. Most OS and development platforms come with a ... (5) ###
> - package manager
> - npm
> - yarn
> - pip
> - Nuget
> - apt in Ubuntu
### 45. Ubuntu package manager is ... ###
> - apt // is newer
> - apt-get // advanced package tool
### 46. Install/remove nano ###
> - apt update // update package DB
> - apt install nano
> - apt remove nano
### 47. In Linux we have a package ... that might contain hundreds of packages, but not all these packages are installed If you want to see all the packages in this DB we run ... and for update DB we run ... ###
> - database
> - apt list
> - apt update
### 48. before installing a package, you should always run ... ###
> apt update
### 49. clear the screen(CLI) with ... ###
> - clear command
> - Ctrl + k
### 50. In Linux, just like Windows are files and directories are organized in a ... in a ... structure. ###
> - Tree
> - Hierarchical
### 51. hierarchical structure in windows? ###
> we have a structure like this with C drive on top of the hierarchy. Then below that we have directories like Program Files, Windows, and so on.
### 52. hierarchical structure in Linux? 9 ###
> In Linux, we have the root directory on top of the hierarchy below and a bunch of standard directories.
> 
> bin / boot / dev / etc / home / root / lib / var / proc
### 53. Which folder in Linux? <br> 1- includes binaries or programs <br> 2- includes all the files related to booting ###
> 1. bin
> 2. boot
### 54. Which folder is in Linux? <br> it's short for devices. So in Linux, everything is a file, including devices, directories, network sockets, pipes, and so on. So the files that are needed to access devices stored in this directory ###
> dev
### 55. Which folder is in Linux? <br> this is short for ... So this is where we have configuration files. ###
> editable text configuration (ETC)
### 56. Which folder is in Linux? <br> This is where ... directories for users are stored. So on a machine with multiple users, each user is going to have a ... directory here. ###
> home
### 57. Which folder is in Linux? <br> We also have ... which is the home directory of the ... user, only the ... user can access this directory. ###
> root
### 58. Which folder is in Linux? <br> which is used for keeping library files like software library dependencies. ###
> lib
### 59. Which folder is in Linux? <br> which is short for ... And this is where we have files that are updated frequently, like lock files, application data, and so on. ###
> variable / var
### 60. Which folder is in Linux? <br> Includes files that represent running processes. ###
> proc
### 61. in Linux, everything is a ... <br> like processes, devices, even directories are ... ###
> file, files
### 62. CMD: Where we are in filesystem? ###
> - PWD (print working directory)
### 63.  CMD <br> 1- see the files and directories on multiple lines <br> 2- see the files and directories on item per line <br> 3- see the files and directories on long list ###
> - ls
> - ls -1
> - ls -l
### 64. CMD: change the current directory <br> relative , absolute? <br> level up 1 and 2 ###
> relative pah is relative to where we are. So in this root directory, we have directories like bin, boot, and so on.
cd etc/a
>
> an absolute path always starts from the root directory. cd /home/a
> - cd ..
> - cd ../..
### 65. in ls cmd result. <br> 1- blue item is? <br> 2- white item is? ###
> 1. directory
> 2. file
### 66. Which folder have the CMD? ###
> bin. like PWD
### 67. short way to go to the home dir? <br> tip? if we are a normal user or root user? ###
> - cd ~
> - normal user go to home
> - root user go to root
### 68. CMD: Create a directory ###
> mkdir test
### 69. cmd: rename and move files & directory ###
> mv a /etc/b
### 70. cmd: only create file ###
> - touch a.txt
> - touch a.txt b.txt
### 71. how remove entire word in on step in CLI? ###
> ctrl + w
### 72. cmd: remove one or more files and remove dir ###
> - rm a.txt
> - rm a.txt b.txt
> - rm *.txt
> - rm -r dirName
### 73. cmd: editing & viewing files 5 ###
> - nano
> - cat = concatenate
> - more
> - less
> - head -n 5 a.txt
> - tail -n 5 a.txt
### 74. One of the important concepts in Linux is the concept of standard input and output. So standard input represents the ..., and standard output represents the .... But we can always change the source of the input or the output. This is called ... 2 ##
> - keyboard
> - screen
> - redirection
> - output <
> - input >
### 75. redirection ex <br> 1- what's i/o in this cmd: cat a.txt <br> 2- all content a.txt to b.txt (cat) <br> 3- all content a.txt to b.txt to c.txt (cat) <br> 4- add hello to a.txt (echo) <br> 5- result of ls long result to a.txt ###
> 1. input keyboard(file) / screen
> 2. cat a.txt > b.txt
> 3. cat a.txt b.txt > c.txt
> 4. echo hello > a.txt
> 5. ls -l > a.txt
### 76. <br> 1- search a string in a file with cmd? <br> 2- search "hello" in file1.txt <br> 3- search "Hello" in file1.txt // insensitive <br> 4- search "hello" in 2 files <br> 5- search "hello" in pattern <br> 6- search "hello" in the current directory <br> 7- search "hello" in a directory <br> 8- how can write it in another way <br> grep -i -r /etc ###
> 1. grep = global regular expression print // it's mouthful
> 2. grep hello file1.txt
> 3. grep -i Hello file1.txt // I = case insensitive
> 4. grep -i hello a.txt b.txt
> 5. grep -i hello file*
> 6. grep -i hello .
> 7. grep -ir /etc
> 8. grep -ir /etc = combine multiple options
### 77. <br> 1- find the list of files & directories(+ hidden) recursively <br> 2- find only directory <br> 3- find only files <br> 4- find all files that start with f <br> 5- find all files that start with f (case insensitive) <br> 6- find all Python files and write the result in a file ###
> 1. find
> 2. find -type d
> 3. find -type f
> 4. find -type f -name "f*"
> 5. find -type f -iname "F*"
> 6. find / -type f - name "*.py" > files.txt
### 78. <br> 1- chaining command and continue if exist error in one command <br> 2- If an existing error does not execute other commands <br> 3- make a directory test and if exists echo exists <br> 4- list files in /bin to less command <br> 5- split long commands in multiple lines ###
> 1. mkdir test; cd test; echo done
> 2. mkdir test && cd test && echo done
> 3. mkdir test || echo "exists"
> 4. pipeline = ls /bin | less
> 5. mkdir hello;\
cd hello;\
echo done
### 79.  ###
### 80.  ###
### 81.  ###
### 82.  ###
### 83.  ###
### 84.  ###
### 85.  ###
### 86.  ###
### 87.  ###
### 88.  ###
### 89.  ###
### 90.  ###
### 91.  ###
### 92.  ###
### 93.  ###
### 94.  ###
### 95.  ###
### 96.  ###
### 97.  ###
### 98.  ###
### 99.  ###
### 100. ###



### 207. Docker Login in CLI ###
> docker login -u user-name -p password
### 208. ... ###
> ...

