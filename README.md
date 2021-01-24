# Docker-installation

#	Install docker on amazon linux/amazon linux 2
		-	yum install -y docker 
		-	service docker start
		
#	Install docker on ubuntu

#	Install docker on RHEL
		- 	sudo dnf config-manager --add-repo=https://download.docker.com/linux/centos/docker-ce.repo

![image](https://user-images.githubusercontent.com/54719289/105633807-d22e3300-5e80-11eb-8322-8a5001bcdc31.png)

      
    - 	sudo dnf repolist -v
		- 	dnf list docker-ce --showduplicates | sort -r
		-	sudo dnf install docker-ce-3:18.09.1-3.el7
		-	sudo dnf install --nobest docker-ce
		
		Install the latest available containerd.io package manually
			-	sudo dnf install https://download.docker.com/linux/centos/7/x86_64/stable/Packages/containerd.io-1.2.6-3.3.el7.x86_64.rpm
			-	sudo dnf install docker-ce
			-	sudo systemctl disable firewalld
			-	sudo systemctl enable --now docker
			-	systemctl is-active docker
			-	systemctl is-enabled docker
		Instaling docker-compose:
			-	curl -L "https://github.com/docker/compose/releases/download/1.23.2/docker-compose-$(uname -s)-$(uname -m)" -o docker-compose
				Once the binary is downloaded, we move it into /usr/local/bin and we make it executable:
			-	 sudo mv docker-compose /usr/local/bin && sudo chmod +x /usr/local/bin/docker-compose
			
		Per-user installation
			sudo dnf install python3-pip
			pip3.6 install docker-compose --user
		
		Test docker:
			sudo docker run --rm --name=linuxconfig-test -p 80:80 httpd


#	dockerize java 
#	dockerize python
#	dockerize nodejs
#	dockerize React
