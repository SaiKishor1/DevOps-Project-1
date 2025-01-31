# DOCKER  PROJECT 

DOCKER FILE	: To create image by automation.

DOCKER COMPOSE	: To create multiple containers on single server.

DOCKER SWARM	: To create single containers on Multiple server.

DOCKER STACK	: Docker swarm + Docker compose

1) CREATE 2 UBUNTU SERVERS T2.MEDIUM AND INSTALL DOCKER ON ALL OF THEM & CREATE CLUSTER OF IT


![Image](https://github.com/user-attachments/assets/cc9f8bec-145f-4e8d-8085-d8619e264041)




2) INSTALL DOCKER

sudo apt update

sudo apt install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

sudo systemctl start docker

sudo systemctl status docker

docker swarm init 

docker node ls



3) INSTALLING JENKINS (MASTER)
   
sudo apt update

sudo apt install fontconfig openjdk-17-jre

java -version

sudo wget -O /usr/share/keyrings/jenkins-keyring.asc \

  https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key
  
echo "deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc]" \

  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  
  /etc/apt/sources.list.d/jenkins.list > /dev/null
  
sudo apt-get update

sudo apt-get install jenkins

build the pipelline 



![Image](https://github.com/user-attachments/assets/1a3aa555-b90f-4c1b-baff-c5442704ff86)





4)TRIVY INSTALLATION:

sudo apt-get install wget apt-transport-https gnupg lsb-release

wget -qO - https://aquasecurity.github.io/trivy-repo/deb/public.key | sudo apt-key add -

echo deb https://aquasecurity.github.io/trivy-repo/deb $(lsb_release -sc) main | sudo tee -a /etc/apt/sources.list.d/trivy.list

sudo apt-get update

sudo apt-get install trivy




5) CREATE CUSTOM IMAGES AND PUSH TO DOCKERHUB WITH TAGS USING DOCKERFILE

6)   GIVE PERMISSIONS

chmod 777 /var/run/docker.sock

systemctl daemon-reload

systemctl restart docker.service



![Image](https://github.com/user-attachments/assets/3f32d7c5-2ed1-4a7e-ac18-3bcc38c92f7b)




7) WRITE DOCKER-COMPOSE.YML FILE AND PUSH TO GITHUB



DOCKER STACK:

Docker stack is used to create multiple services on multiple hosts. i.e it will create multiple containers on multile servers with the help of compose file.

To use the docker stack we have initialized docker swarm, if we are not using docker swarm, docker stack will not work.

once we remove the stack automatically all the containers will gets deleted.

We can share the containers from manager to worker according to the replicas

Ex: Lets assume if we have 2 servers which is manager and worker, if we deployed a stack with 4 replicas. 2 are present in manager and 2 are present in worker.

Here manager will divide the work based on the load on a server

COMMAND:

TO DEPLOY : docker stack deploy --compose-file docker-compose.yml stack_name

TO LIST : docker stack ls

TO GET CONTAINERS OF A STACK : docker stack ps stack_name

TO GET SERVICES OF A STACK: docker stack services stack_name

TO DELETE A STACK: docker stack rm stack_name


PORTAINER:

it is a container organizer, designed to make tasks easier, whether they are clustered or not. 

abel to connect multiple clusters, access the containers, migrate stacks between clusters

it is not a testing environment mainly used for production routines in large companies.

Portainer consists of two elements, the Portainer Server and the Portainer Agent. 

Both elements run as lightweight Docker containers on a Docker engine


SETUP:

Must have swarm mode and all ports enable with docker engine

curl -L https://downloads.portainer.io/ce2-16/portainer-agent-stack.yml -o portainer-agent-stack.yml

docker stack deploy -c portainer-agent-stack.yml portainer

 docker ps
 
public-ip of swamr master:9000


![Image](https://github.com/user-attachments/assets/36b4aeba-388c-4341-819f-c55b46fb2dbb)






