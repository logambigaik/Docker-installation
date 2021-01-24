# History before containerization
		>>	Virtual Machine
		>>	This VM will run mutiple application on the same physical hardware & this is nothing but virtualization
		
	Drawbacks:
		>> Bulk in size
		>> When we run mutiple appln this give performanceissue 
		>> boot up time will be longer than usual
		

#For CICD , we need containerization ,its not physical hardware level,system level

Containerization:
============
	is also virtualization but operating on system level.
	
Reason to use container:
=================
		>>	Container will not have guest os and use host os directly so they will share relevant libraries and resources when needed
		>>	Processing and execution on each application are very fast since each application using it's specific binaries and the application libraries are on the kernel so its very fast
		>>	Booting of a container takes only fraction of second because containers are lightweight and faster than virtual machine.
		
		
What is docker:
==========
		>>	Docker is a platform which packages application and its dependencies in the form of containers
		>>	Containerization cocnept ensures that appl will work in any environment. like development, QA , UAT  and Prod environment
		>>	Developer build a container having different application installed on it & give it to the QA or TEST team . QA team only run the container to replicate the environment in QA environment.
		

# Terminology involved:
===============
			>> Docker file
			>> Docker image
			>> Docker container


Docker FIle:
========
>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
									Sample Java Dockerfile
>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
FROM java:8
VOLUME /tmp
ADD dockerapp-0.0.1-SNAPSHOT.jar app.jar
RUN bash -c 'touch /app.jar'
ENTRYPOINT ['java','-Djava-security-egd=file:/dev/./urandom','-jar','/app.jar']
>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>

##########################################################################################################################################################################
						Build								 		Run
Docker FIle =========>Docker Image==============>Docker CONTAINER	
##########################################################################################################################################################################

>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
									Sample Python Docker file
>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
FROM python:alpine3.7
COPY . /app
WORKDIR /app
RUN pip install -r requirements.txt
EXPOSE 5001
ENTRYPOINT ['python']
CMD ['app.py']
#########################################################################################################################################################################

Docker image:
==========
			Docker image is nothing but a read only template, using docker run will run the image and create the container for that image.
			Docker images will be stored in docker registry ,
						it can be  
										user local repository, 
										public repo like docker hub (private repo is in but due to replication company is not using . DOcker hub organization need to create hence companies are using other private repo)
										or private repo like ECR-Elastic container registry or acr=Azure container registry ,gcr=Google container registry
			WE can integrate nexus with docker, will it be private
			
Docker CONTAINER:
===============
			Is a running instance or copy of a docker image  and these are ready application created from docker images which is the use case of docker

################################################################################################################################################################################
# Docker compose:
===========
	is a yaml file  which contains details about the services,volume and network. Using docker container we can create a seperate container for db and application. It perfectly worked on single node.

Sample yaml file:
>>>>>>>>>>>
		version: '3.3'

services:
   db:
     image: mysql:5.7
     volumes:
       - db_data:/var/lib/mysql
     restart: always
     environment:
       MYSQL_ROOT_PASSWORD: somewordpress
       MYSQL_DATABASE: wordpress
       MYSQL_USER: wordpress
       MYSQL_PASSWORD: wordpress

   wordpress:
     depends_on:
       - db
     image: wordpress:latest
     ports:
       - "8000:80"
     restart: always
     environment:
       WORDPRESS_DB_HOST: db:3306
       WORDPRESS_DB_USER: wordpress
       WORDPRESS_DB_PASSWORD: wordpress
       WORDPRESS_DB_NAME: wordpress
volumes:
    db_data: {}
	
>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>

# Docker swarm:
==============
		If we want to Maintain or create cluster of  docker machine or engine we need to use docker swarm.
		Docker machine can be hosted on different nodes and these nodes will be form of cluster when connected with docker swarm.

>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
