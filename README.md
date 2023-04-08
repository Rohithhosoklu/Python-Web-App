Project Name - Building and Deploying a Docker Image for a React-Django Web App on Ubuntu

Step 1: Update the packet manager
In the first step, we need to update the packet manager using the apt-get command in Ubuntu. This will ensure that we have the latest version of the packet manager before we proceed with the installation of Docker.

![image](https://user-images.githubusercontent.com/63364609/230716978-cbfaa401-b4bd-43b6-bf45-39002047b357.png)
 
Step 2: Install Docker
Once we have updated the packet manager, we can install Docker using the apt-get command. This command installs Docker on the Ubuntu operating system.
sudo apt-get install docker.io -y

![image](https://user-images.githubusercontent.com/63364609/230716983-26c98913-0b97-492e-ba78-7385d886f89d.png)


Step 3: Check the Docker version and status
After installing Docker, we can check the Docker version and status to ensure that it has been installed correctly. We can use the “sudo docker — version” command to check the Docker version, and “sudo service docker status” or “systemctl status docker” command to check the status of the Docker service.

For version — sudo docker –version
![image](https://user-images.githubusercontent.com/63364609/230716994-569d8c05-32aa-45e0-aa8a-caf9bb1dcfd8.png)
20.10.21 lastest docker version is going on in market.

For status — sudo service docker status or systemctl status docker
![image](https://user-images.githubusercontent.com/63364609/230716999-9ec67080-bd34-40e0-8932-cdaa5f9dbb30.png)

 Its shows the status as active and it's running.

Step 4: Clone the code from Github
In this step, we clone the code for the Django-React demo app from Github using the “git clone” command. The code will be downloaded and stored in a directory.
Git clone https://github.com/LondheShubham153/react_django_demo_app.git

![image](https://user-images.githubusercontent.com/63364609/230717005-db26e929-9c5d-4964-a1fa-d920ed4cb307.png)


(Here I’m cloning the code from Shubham londhe’s account and even you can forks that Repositorie to your github account)


Step 5: Check the files and understand the requirements

After cloning the code, we can check the files in the directory and understand the requirements needed to run the code. The “ls” command can be used to check the files, and we can refer to the README file and manage.py file to understand the code and its dependencies.
· After doing the clone, a directory will be created with a name called react_django_demo1_app
· Go to that directory and do ls to check files.
Commands
- Cd react_django_demo1_app
- ls
README file — This is the where developer gives steps to run this code.
Here developer has not given much information about the code so we will other files to understand the code.

![image](https://user-images.githubusercontent.com/63364609/230717013-ee91ae84-1e5e-4072-b02e-72644f1b21da.png)


Manage.py file — Generally this is the file that contains the main things and we have to run this file by seeing the extension (.py) we can say this is Python project and we need to install Python to run is code.

![image](https://user-images.githubusercontent.com/63364609/230717021-a65372e9-9743-4d82-a66f-f82efe1bb807.png)

Requirements.txt file — This is file we will get to know all requirements we need to run this code. Here in this project, we need Django also to run it.
 
![image](https://user-images.githubusercontent.com/63364609/230717028-be78a44d-d47c-4242-9e32-13f4cb8a33b5.png)


Step 6: Create a Docker image using a Dockerfile

A Dockerfile is a text file that includes the necessary commands for building a Docker image. In this step, we create a Dockerfile using the “vim Dockerfile” command, and include the necessary commands such as “FROM”, “RUN”, “COPY”, “ENV”, “EXPOSE”, and “CMD”. These commands are used to install packages, create directories, set environment variables, and specify the command to be run when the container is created.

Docker file — It is a text file that has all commands which need to be run for building a given image.
 
![image](https://user-images.githubusercontent.com/63364609/230717035-40ec1c0c-39fe-4929-8d7a-1090bf3daeb0.png)

FROM: This command specifies the base image that the new image will be built on top of. The base image can be an official image from the Docker Hub or a custom image from a private repository.

RUN: This command runs a command in the shell of the container. It is used to install packages, create directories, or perform any other task that needs to be done during the image creation process.

COPY: This command copies files or directories from the host machine to the container.

ENV: This command sets environment variables in the container.

EXPOSE: This command informs Docker that the container listens on the specified network ports at runtime.

CMD: This command specifies the command that will be run when a container is created from the image.

Step 7: Build the Docker image

After creating the Dockerfile, we can build the Docker image using the “docker build” command. This command builds an image from the Dockerfile and tags it with a name and version.

Docker image — They are executable packages, bundled with application code & dependencies, software packages, etc. for the purpose of creating containers. Docker images can be deployed to any docker environment and the container can be spun up there to run the application.
docker build . -t react-django-app:latest
After building the Docker image, we can check the images using the “docker images” command. This command lists all the images that have been built on the Docker environment.

![image](https://user-images.githubusercontent.com/63364609/230717053-68dfb031-90f3-4f91-ac14-e04dcb8c6b9c.png)


- To check images, use command docker images
![image](https://user-images.githubusercontent.com/63364609/230717060-eed3ba7f-3848-4e77-88e7-1ffc44cf700d.png)


Step 8: Create a Docker container

Once we have built the Docker image, we can create a Docker container using the “docker run” command. This command creates a container from the image and maps the container’s port to the host’s port.
Docker container — Container hold the entire package that is needed to run a application, libraries and system dependencies.
- Now using above images we will create a container by using command
docker run -d -p 8000:8000 react-django-app:latest
- -d is daemon mode or detach mode
-p is port mapping of container port 8000 to instance port 8000

![image](https://user-images.githubusercontent.com/63364609/230717082-8e592443-d3c4-475c-a744-3a33d55c2c6f.png)


- We can check the list of Docker containers using the “docker ps” command. This command lists all the running Docker containers.

![image](https://user-images.githubusercontent.com/63364609/230717087-475d8e35-a1fc-47ba-8522-5917b0c1747f.png)

Step 9: Open port 8000 in the instance’s security inbound rule

Before checking the application on a web browser, we need to open port 8000 in the instance’s security inbound rule to allow traffic to flow to the container.
 
![image](https://user-images.githubusercontent.com/63364609/230717095-760adc22-2037-4798-8c82-b9e67c44f49a.png)

Step 10: Check if the application is running

Finally, we can copy the public IP of the instance to the web browser and check if the application is running. If everything has been set up correctly, the Django-React demo app should be up and running.

![image](https://user-images.githubusercontent.com/63364609/230717106-33e45e44-fe19-4afa-bc0d-55930a10ee36.png)

In summary, setting up a Docker container for a Django-React demo app on Ubuntu involves updating the packet manager, installing Docker, cloning the code from Github, understanding the code and its requirements, creating a Dockerfile, building the Docker image, creating a Docker container, checking the list of Docker containers, opening the required port in the instance’s security inbound rule, and checking if the application is running on a browse.
