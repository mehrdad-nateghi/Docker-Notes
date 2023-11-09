# Docker Notes [![Generic badge](https://img.shields.io/badge/Sources-1-<COLOR>.svg)]()            [![Generic badge](https://img.shields.io/badge/Notes-206-<COLOR>.svg)]()
## Sources ##
Title  | Type | Link
------------- | ------------- | -------------
The Ultimate Docker Course  | Video | https://codewithmosh.com/p/the-ultimate-docker-course
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
### 79. just like we have variables in our programming languages, in Linux, we have ... variables, which we can set for storing configuration settings for our applications, or applications can read configuration settings from these environment variables. ###
> environment
### 80. <br> 1- see all env var <br> 2- see value of a var (2) <br> 3- How can set a var for the current session <br> 4- How can set a var persistently ###
> 1. printenv
> 2. printenv PATH / echo $PATH
> 3. export DB_USER=mosh
> 4. with nano
echo DB_USER >> .bashrc
### 81. env var HOSNAME generate automatically by ... ###
> Docker
### 82. which dir os search for cmd and programs ###
> PATH env var
### 83. start a container with ID ###
> docker start -i ID
### 84.every time a user logs in linux loads this command from the user's home directory? ###
> user's personal startup file = .bashrc
In this file we have write permanent env vars
### 85. T/F store sensitive information in .bashrc ###
> F
### 86. all changes to bashrc file are only effective in the next terminal session. solution? 2 ###
> 1. exit this session
> 2. source ~/.bashrc
### 87. a ... is an instance of a running program. ###
> process
### 88. See all running programs or processes & describe results ###
> - 1- ps
> - tty? teletype
> - pts/0 = sudo terminal - first terminal
> - open another terminal window pts/1
> - time = each process consume CPU
### 89. <br> 1- sleep terminal in 3 sec <br> 2- sleep 100 and put in background ###
> 1. sleep 3
> 2. sleep 100 &
### 90. kill a process ###
> kill PID ex: kill 89
### 91. cmd for add, modify, and delete a user ###
> - useradd / adduser
> - usermod
> - userdel
### 92. each option of each cmd may have two options ###
> - short with one hyphen ex: -m 
> - long descriptive with two hypen ex: --create-home
### 93. <br> 1- how to create a user and create home dir <br> 2- where is this user store? ###
> 1. useradd -m john
> 2. in the configuration file in ETC dir cat etc/passwd
### 94. which data store here? etc/passwd ###
> not store password, store user's account information
### 95. where is this info stored and what does it mean? <br> John:x:1001:1002::/home/john:/bin/sh ###
> etc/passwd = store user's account information
> - user = john
> - x = password stored somewhere
> - 1001 = user-id
> - 1002 = id of primary group
> - /home/john = home dir of the user
> - /bin/sh = old original shell program
### 96. how can change /bin/sh to an enhanced version /bin/bash ###
> usermod -s /bin/bash john
### 97. where's the user's password? only access? ###
> - etc/shadow // encrypted format
> - for root user
### 98. run docker with bash for john user ###
> docker exec -it -u john container-id bash
### 99. delete the user john ###
> userdel john
### 100. another cmd for add user is ... and what's different? which one is better for using in docker? why? ###
> - useradd = original app / since we can't use interact with adduser 
> - adduser = perl script is more interactive / add user, group with the same name, home dir, set password
### 101. cmd for managing group 3 ###
> groupadd / groupmod / groupdel
### 102. <br> 1-add new group developers <br> 2- where's the new group? describe content ###
> 1. groupadd developers
> 2. /etc/group
developers:x:1003
name of the group and 1003 is the id of the group
### 103. <br> 1- how add john to the developer group <br> 2- how change primary group of john ###
> 1. usermod -G developers john
> 2. usermod -g main john
### 104. why do we need a group? ###
> group is like a role and each role has many permissions. then each user can have many groups.
### 105. each user of Linux has many groups? what are these? ###
> one primary and many secondary groups
### 106. show a list of groups of a user ###
> groups john
### 107. structure of permissions ###
> - drwxr-xr-x
> - it has 4 parts
> - first letter form left
> d = directory
> f = file
> - 3 groups that has 3 characters
> - first group = for user who owns the file (root)
> - second = for group who owns the file (root)
> - third = for other
> - in each group has 3 chars
> - first = r = read
> - second = w = write
> - third = x = execute
> - fourth = - = nothing
### 108. what does x permission mean for the directory? ###
> go to dir with cd
### 109. all directory has this permission? ###
> x
### 110. in chmod how can set for which one group we want to change mode? ###
> - u = user
> - g = group
> - o = other
### 111. add x permission to user ###
> chmod u+x
### 112. green file in ls cmd mean? ###
> execute file like deploy.sh
### 113. how can add x and w and remove r to other and group? ###
> chmod og+x+w-r a.txt
### 114. When we create two containers with the same image, we have? ###
> two different containers with their own file system. and hidden from other container. we will learn about share data between container.
### 115. Dockerfile instructions <br> for specifying the base image. So we take that base image which contains a bunch of files and directories, and then we build on top of it. ###
> FROM
### 116. Dockerfile instructions <br> for specifying the working directory. Once we use this command, all the following commands will be executed in the current working directory. ###
> WORKDIR
### 117. Dockerfile instructions <br> we have ... and ... for copying files and directories. ###
> - COPY
> - ADD
### 118. Dockerfile instructions <br> for executing operating system commands. So all the Linux commands that we talked about in the previous section, you can execute them using ... Now if you're on Windows, you can execute Windows commands using ... as proc. ###
> RUN
### 119. Dockerfile instructions <br> for setting environment variables ###
> ENV
### 120. Dockerfile instructions <br> for telling Docker, that our container is starting on a given port ###
> EXPOSE
### 121. Dockerfile instructions <br> for specifying the user that should run the application. Typically, we want to run our application using a user with limited privileges. ###
> USER
### 122. Dockerfile instructions <br> ... & ... for specifying the command that should be executed when we start a container. ###
> - CMD
> - ENTRYPOINT
### 123. ... can be an operating system like Linux or Windows, or it can be an operating system plus a runtime environment. ###
> The base image / FROM ...
### 124. Where can I find the sample base image? ###
> https://docs.docker.com/samples/
### 125. <br> Where we type full url for the base image? <br> and Why don't set a full url? and Why we don't set node:latest ###
> - it doesn't exist in docker hub for ex: mcr.microsoft.com/image / mcr: microsoft container registery
> - since it can be change. it's better set specific version. even not latest since our app can not run with the latest version
### 126. tip about the base image <br> 1- os/arch <br> 2- compress size ###
> - docker automatically sets the right image with os/arch
> - it's compress size and after download it can be more than it.
### 127. <br> 1- build image for react-app <br> 2- run image & run shell ###
> 1. docker build -t tag-react-app .
    . = where is the docker file
> 2. docker run -it tag-react-app sh
### 128. base image is = node:alipne <br> run this = 2- docker run -it tag-react-app bash <br> ? ###
> error
> apline has not bash
> we should write = sh
### 129. build context? ###
> docker build -t imageName .
A period (.) means the current directory. So when we execute this command, Docker client sends the content of this directory to Docker engine. This is called the build context. So Docker client sends the build context to Docker engine, and then Docker engine will start
executing these commands one by one. So at that point, Docker
engine does not have access to any files, or directories out this directory.
### 130. Docker instruction <br> COPY <br> 1- copy package.json to /app <br> 2- if /app not exists? <br> 3- copy a.txt b.txt to /app <br> 4- copy a.txt b.txt to /app (t/f) <br> 5- copy all file "a*.txt" to /app <br> 6- copy everything from the current directory to /app <br> 7- how can set a relative path? tip? we can replace it with ... <br> 8- copy hello world.txt to . ###
> 1. COPY package.json /app
> 2. Docker create it automatically
> 3. COPY a.txt b.txt /app/
> 4. if we set one more file we should add / in the end of destination (3 is correct)
> 5. COPY a*.txt /app/
> 6. COPY . /app/
> 7. WORKDIR /app // all cmd after this run in /app
> replace it with .
> COPY . .
> 8. COPY ["hello world.txt","."] // each item show an argument of copy cmd
### 131. What's diff between ADD & COPY <br> which one is safer? ###
> - add has two more features
> 1. copy from URL
ADD HTTP://.../... /app
> 2. uncompress zip automatically
ADD TTP://.../a.zip /app
> - safer= copy
### 132. When we set WORKDIR /app <br> When we run = docker run -it app sh <br> PWD? ###
> /app
### 133. How to exclude node_modules folder in docker ###
> - in .dockerignore add node_moduels/
> - dockerignore = all lowercase
### 134. execute <br> npm install in docker file ###
> RUN npm install
### 135. if the base image is alpine <br> if we RUN apt install <br> then? ###
> we get an error since alpine doesn't have apt it has apk
### 136. Set env variable (2) <br> API_URL http://api.myapp.com <br> which way is better ###
> 1. ENV API_URL=http://api.myapp.com
> 2. ENV API_URL http://api.myapp.com
> - 1 IS BETTER
### 137. How to define: container listen to port 3000 ###
> in dockerfile: EXPOSE 3000
### 138. docker default run image by ... user ###
> root
### 139. in alpine <br> 1- add user app <br> 2- add it to app group primary <br> 3- create a system user <br> 4- set all commands run by this user ###
> - RUN addgroup app && adduser -S -G app app
> - USER app
### 140. defining a group , a user and set user must be placed at the ... of the docker file otherwise we should get a permission error. ###
> top
### 141. 1- How can run the app with this "npm start" (2) <br> 2- If we have some CMD in the docker file, which one runs? ###
> 1. docker run app npm start
in docker file = CMD npm start
> 2. the latest
### 142. Run vs CMD ###
> - Run = run at the time of building the image
> - CMD = runtime, executed when starting a container
### 143. Describe shell form and execute form for CMD. and differences? which one is better? ###
> - shell form = CMD npm start
docker will execute this inside a separate shell
in Linux(/bin/sh)
in windows(cmd)
> - Exec form = CMD ["npm","start"]
it's better
run directly, there no need to spin off the shell
### 144. CMD vs ENTRYPOINT ###
> - both have shell and exec form
cmd = We can change the default cmd
docker run app sh
> - for entrypoint we should run it for change
docker run app --entrypoint sh
> - cmd(exec form) it's better and simple for use
### 145. if docker file changed, we must ... image again. ###
> build
### 146. An image is collection of ..., that is ... that only includes ... files ###
> - layers
> - small file systems
> - modified
### 147. How docker create layer?
###
> execute each instruction in docker file and create a new layer. The layer is result of the instruction.
### 148. some instruction may be have many layers for ex?
###
> FROM node:1 
> 
> since multiple files modified
### 149. How to show layers of the image? ###
> Docker history imageName
### 150. describe optimization when build an image that docker uses. ex? ###
> if it has not changed then docker uses this layer from cache.
> before 
> - COPY . . 
> - RUN npm install <br>
> after
> - COPY package*.json
> - RUN npm install
> - COPY . .
### 151. RUN npm update <br> docker rebuild or not? ###
> Always rebuild
### 152. Where we can see docker use cache for an instruction or not? ###
> When we build an image we can show log
CACHED [2/6]
### 153. the best strategy for write docker file for optimization ###
> - stable instructions (top) ... Changing instructions
### 154. <br> 1. How to remove the unused image(dangling) <br> 2. How to remove the unused container(dangling) <br> 3. How to remove app image ###
> 1. docker image prune
> 2. docker container prune
> 3. docker image rm app name2 name3
### 155. whenever we build an image or pull it from the Docker hub, by default, docker uses the ... tag. it's just a label and it doesn't mean it's the ... version of the image. if you don't tag your image properly, ... can point to an older version. the ... tag fine for ... and you shouldn't use it for or ... ###
> latest
latest/ development / production or staging
### 156. tag an image (2) ###
> 1. when we build it
> - docker build -t app:buster . / app:1.2.3 / app:88
> - docker images / we see 2 tags latest and new tag then = docker image remove app:88
> 2. after build
> - docker images tag app:latest[image id] app:88
### 157. It's so important when we have an image with tag 88 and the latest and build another image with a new tag, latest doesn't point to a new image. we should point latest to new image How? ###
> docker image tag app:99 app:latest
### 158. We can create a repository in docker hub and connect it to github or bitbucket. and every time we push new code. docker hub ... pull the latest code and build a new image. ###
> automatically
### 159. How to push the image to docker hub ###
> 1. create a repo = mnateghi/app
> 2. docker image tag app:2 mnateghi:2
> 3. docker login
> 4. docker push mnateghi/app:2
### 160. Saving and loading image ###
> - saving: docker image save -o app-image.tar app:3
> - load: docker image load -i app-image.tar
### 161. running container <br> 1. simple <br> 2. run in the background <br> 3. to give a custom name <br> 4. to publish a port HOST:CONTAINER ###
> 1. docker run <image>
> 2. docker run -d <image>
> 3. docker run —name <name> <image>
> 4. docker run —p 3000:3000 <image>
### 162. Viewing the logs <br> 1- simple just show and close <br> 2- to follow the log <br> 3- to add timestamps <br> 4- to view the last 10 lines ###
> 1. docker logs <containerID>
> 2. docker logs -f <containerID>
> 3. docker logs —t <containerID>
> 4. docker logs —n 10 <containerID>
### 163. Docker exec vs run ###
> - run = start a container
> - exec = executing in running container
### 164. Executing commands in running containers. <br> execute a cmd shell ###
> - docker exec <containerID> <cmd>
> - ex: docker exec -it <containerID> sh
### 165. when you execute a cmd in running container in interactive mode and you exit, the container is ... ###
> is running and not stop
### 166. Starting and stopping containers ###
> - docker stop containerID
> - docker start containerID
### 167. docker start vs run ###
> - start = start a stopped container
> - run = start a new container
### 168. Removing containers <br> 1- long cmd <br> 2- short cmd <br> 3- to force the removal of the running container <br> 4- to remove stopped containers ###
> 1. docker container rm <containerID>
> 2. docker rm <containerID>
> 3. docker rm -f <containerID> # to force the removal
> 4. docker container prune # to remove stopped containers
### 169. search in all name of container for c1 ###
> docker ps -a | grep c1
### 170. each container has its own ... that is invisible to other containers. When we delete a container all ... also delete. we don't save data in ... we use ... ###
> - file system
> - files
> - container
> - volume
### 171. ... is a storage outside of the container. It can be a ... on the host or somewhere on the ... ###
> - Volume
> - Directory
> - Cloud
### 172. Volumes <br> 1- list <br> 2- create <br> 3- inspect for <br> 4- map host dir to image when run image ###
> 1. docker volume ls
> 2. docker volume create app-data
> 3. docker volume inspect app-data
> 4. docker run -v app-data:/app/data <image>
### 173. Where we can see this info about <br> - volume <br> - driver <br> - mountpoint <br> scope and etc ###
> docker image inspect
### 174. How can place volume in the cloud ###
> there's a driver for it we can find it.
in docker volume inspect drive = local mean local host
### 175. run docker <br>  1- detach mode <br> 2- map 4000 to 3000 <br> 3- map volume app-data to /app/data
###
> docker run -d -p 4000:3000 -v app-data:/app/data name-image
### 176. docker run -d -p 4000:3000 -v app-data:/app/data name-image <br> what's the problem if the data directory does not exist? ###
> docker creates it automatically but it does not have the right permission to write.
it's better we make it before in docker file after user app after workdir
run mkdir data
### 177. How can share a volume between many containers ###
> map all container to one folder
### 178. Copying files between the host and containers 2 ###
> - docker cp source destination
> - docker cp <containerID>:/app/log.txt .
> - docker cp secret.txt <containerID>:/app
### 179. Sharing source code with containers <br> 1-for production <br> 2- for development (3 way) which on is the best ###
> 1. build a new image
> 2. build a new image
> - copy files
> - map /project(host) to /app(container) = is the best
### 180. Sharing source code with containers - cmd ###
> docker run -v $(pwd):/app <image>
### 181. ... built-in on top of the docker engine. it installs by default with docker desktop for Win & Mac. it helps to ... we can check the version of it by ... ###
> - docker-compose
> - start the app with multiple containers
> - docker-compose --version
### 182. clean up workspace (images / containers) <br> - in cli <br> - in docker desktop ###
> - docker container rm -f $(docker container ls p -aq)
> - docker image rm -f $(docker image ls p -q)
> - clean / purge data
### 183. convert it to yaml ###
```json
{
"name": "Docker",
"boolean": true,
"tags": ["software", "devops"],
"number": 123,
"object": {
"a": "b",
"c": "d"
},
}
```
```yaml
---
name: Docker
boolean: true
tags:
- software
- devops
number: 123
object:
a: b
c: d
```
### 184. parsing ... file is slower than ... file. because the parser doesn't know the price: 149 is a string or number. It reads everything as a string and tries to evaluate it. but in ... all value has type ex: "name": "ali" is a string and don't need to evaluate it. ###
> - yaml
> - JSON
> - JSON
### 185. Describe ###
```yaml
describe

version: "3.8"

services:
  frontend:
    depends_on: 
      - backend
    build: ./frontend
    ports:
      - 3000:3000

  backend: 
    depends_on: 
      - db
    build: ./backend
    ports: 
      - 3001:3001
    environment: 
      DB_URL: mongodb://db/vidly
    command: ./docker-entrypoint.sh

  db:
    image: mongo:4.0-xenial
    ports:
      - 27017:27017
    volumes:
      - vidly:/data/db

volumes:
  vidly:
```
```yaml
version: "3.8" // use the latest version

services:
  frontend:
    depends_on: 
      - backend
    build: ./frontend // where's dockerfile
    ports:
      - 3000:3000

  backend: 
    depends_on: 
      - db
    build: ./backend
    ports: 
      - 3001:3001
    environment: 
      DB_URL: mongodb://db/vidly
    command: ./docker-entrypoint.sh

  db:
    image: mongo:4.0-xenial // download image
    ports:
      - 27017:27017 // default port
    volumes:
      - vidly:/data/db // /data/db default path of mongodb

volumes:
  vidly:
```
### 186. all command we use with docker, we can use with docker-compose and different? ex? ###
> - docker build
> - docker-compose build
> - docker-compose run on multiple containers
### 187. docker composer - by all images prefixed with the name of ... ex? ###
> - application
> - vidly_api / vidly_web
### 188. force rebuild the image with docker compose ###
> docker-compose build --no-cache
### 189. docker-compose ps <br> docker ps ###
> - show all containers in this app
> - show all containers from all app
### 190. start and stop the project by docker compose <br> start and build and detach mode? ###
> - docker-compose up
> - docker-compose up --build -d
> - docker-compose down
### 191. meaning of column "command " in this cmd? <br> docker-compose ps ###
> which command is use to run the service
### 192. docker-compose ... create a network and add our ... on that network. So these ... (2) can talk to each other with their ... ###
> - automatically
> - containers
> - containers / host(API,web,db)
> - name (API,web,db)
### 193. where can we see the name of the network? (2) ###
> - docker-compose up -d
> - can see the default name of the network: vidly_default
> - docker network ls
### 194. ping API from web, what happened under the hood? ###
> - docker exec -it -u root conainerID sh
ping API
> - docker comes with an embedded DNS server that contained the name and IP of containers.
Inside each container we have a component called the DNS resolver that talks to the DNS server to find the IP of target container.
> - ping API
> - 1. DNS resolver asks from DNS server: IP of API?
> - 2. DNS server answers: ip
### 195. each container has an ... address that is part of a network. ###
> IP
### 196. cmd: see IP of current container ###
> ifconfig
### 197. docker-compose <br> 1- show all logs of the container of the app <br> 2- only web container ###
> 1. docker-compose logs
> 2. docker logs containerIdOfweb -f
### 198. docker-compose <br> publish changes for API with volume ###
```yaml
API:
volumes:
- ./backend:/app
```
### 199. <br> 1- overwrite cmd in docker file in docker-compose.yml <br> 2- run migrate mongo & npm start <br> 3- solve the problem. <br> 4- refactor ###
> 1. command
> 2. command: migrate-mongo up && npm start
> 3. command: ./wait-for db:27017 && migrate-mongo up && npm start
> 4. command: ./docker-entrypoint.sh
### 200. run test inside the app is ... it's better run a ... for run test. ex?  ###
> - slow
> - a new service = container
```yaml
web-test:
image: vidly_web
volumes:
- ./frontend:/app
  command: npm test
```
### 201. To deploy our dockerized application we have ... options. ? ###
> 1. Single-host deployment
> 2. Cluster deployment: a group of servers
### 202. single-host vs cluster deployment ###
> - single-host: deployment is easy / server down our app will not be accessible / if our users grow then our server cannot handle that load.
> - cluster: get high availability and scalability.
### 203. run cluster needs special tools called ... docker has its own tool and built-in that is called ... but it's not popular and most people use ... ###
> - orchestration
> - Docker swarm
> - Kubernetes: google product
### 204. VPS options? ###
> - virtual private server
> - Digital Ocean
> - Google Cloud Platform(GCP)
> - Microsoft Azure
> - Amazon Web Services (AWS)
### 205. What's a docker machine? download? ###
>docker-machine on the dev device talks to the docker engine on the server. we can run the docker cmd in our cli and our cmd sent to docker engine on our server.
> - https://github.com/docker/machine/releases
### 206. we need create another docker compose file for production. name? ###
> docker-compose.prod.yml
### 207. Docker Login in CLI ###
> docker login -u user-name -p password