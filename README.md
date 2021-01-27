# Docker-installation

#	Install docker on amazon linux/amazon linux 2
		-	yum install -y docker 
		-	service docker start
	or
		-	amazon-linux-extras install docker -y
		-	rpm -qa | grep docker
		-	service docker start
		-	service docker status
		
#	Install docker on ubuntu
		- 	apt update
		-	apt install docker.io
			docker --version
![image](https://user-images.githubusercontent.com/54719289/105640081-1847be80-5ea2-11eb-97d9-e0257227f235.png)
		-	service docker start
![image](https://user-images.githubusercontent.com/54719289/105640166-842a2700-5ea2-11eb-9c88-74c64bb11571.png)
	
		
#	Install docker on RHEL
	
	
   	 	-	sudo yum install -y yum-utils
		
		-	sudo yum-config-manager     --add-repo     https://download.docker.com/linux/centos/docker-ce.repo
    		
		-	yum list docker-ce --showduplicates | sort -r
    		
		-	yum list docker-ce-cli --showduplicates | sort -r
    		
		-	sudo yum install docker-ce-19.03.13-3.el8.x86_64  docker-ce-cli-19.03.13-3.el8.x86_64 containerd.io
    		
		-	rpm -qa | grep docker
    		
		-	service docker start
		
![image](https://user-images.githubusercontent.com/54719289/105912370-64853100-6051-11eb-9cab-94d5060c5a83.png)
		
		-	service docker stop
    		
		-	yum install -y container-selinux containerd.io docker-ce-cli-19.03.13-3.el8.x86_64 iptables libcgroup
		
		-	service docker start

![image](https://user-images.githubusercontent.com/54719289/105912495-8e3e5800-6051-11eb-9e6b-6f04831b5a8f.png)


#	dockerize java
		- sample docker file for java with existing image
		  
		  FROM java:8
		  RUN bash -c 'mkdir app'
		  COPY ./target/*.jar /app/app.jar
		  ENTRYPOINT ['java','-jar','/app/app.jar']	
			
#	dockerize python
		
		 FROM python:alphine3.7
		 COPY . /app
		 WORKDIR /app
		 RUN pip install -r requirements.txt
		 EXPOSE 5001
		 ENTRYPOINT ["python"]
		 CMD["demo.py"]
		 
#	dockerize nodejs

#	dockerize React
