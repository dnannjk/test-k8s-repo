Install the AWS CLI version 2 on Linux | How to Install the AWS CLI version 2 on Linux
Follow these steps from the command line to install the AWS CLI on Linux.

curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip" 

sudo apt install unzip

sudo unzip awscliv2.zip  

sudo ./aws/install

aws --version

Install kubectl on Ubuntu Instance | How to install kubectl in Ubuntu
Kubernetes uses a command line utility called kubectl for communicating with the cluster API server. It is tool for controlling Kubernetes clusters. kubectl looks for a file named config in the $HOME directory.

How to install Kubectl in Ubuntu instance
Download keys from google website
curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -

Create the below file
sudo touch /etc/apt/sources.list.d/kubernetes.list

echo "deb http://apt.kubernetes.io/ kubernetes-xenial main" | sudo tee -a /etc/apt/sources.list.d/kubernetes.list

Update package manager
sudo apt-get update

Install
sudo apt-get install -y kubectl

Verify if kubectl got installed
kubectl version --client

Install eksctl on Linux Instance | How to install eksctl in Ubuntu
eksctl is a command line tool for working with EKS clusters that automates many individual tasks.

The eksctl tool uses CloudFormation under the hood, creating one stack for the EKS master control plane and another stack for the worker nodes.

Download and extract the latest release of eksctl with the following command.

curl --silent --location "https://github.com/weaveworks/eksctl/releases/latest/download/eksctl_$(uname -s)_amd64.tar.gz" | tar xz -C /tmp

Move the extracted binary to /usr/local/bin. 

sudo mv /tmp/eksctl /usr/local/bin

eksctl version


Install Docker Ubuntu | How to install Docker in Ubuntu 22.0.4 | Setup Docker on Ubuntu
Please find steps needed for installing Docker in Ubuntu 22.0.4 instance. You can install in Docker in many ways. But try only one option.

Docker installation steps using default repository from Ubuntu
Update local packages by executing below command:
sudo apt update

Install the below packages
sudo apt install gnupg2 pass -y

gnupg2 is tool for secure communication and data storage. It can be used to encrypt data and to create digital signatures
 
Install docker
sudo apt install docker.io -y

Add Ubuntu user to Docker group
sudo usermod -aG docker $USER

We need to reload shell in order to have new group settings applied. Now you need to logout and log back in command line or execute the below command:
newgrp docker

The Docker service needs to be setup to run at startup. To do so, type in each command followed by enter:

sudo systemctl start docker
sudo systemctl enable docker
sudo systemctl status docker

Docker installation steps using Official Docker Repository (Alternative installation steps)

sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
sudo apt-get update
sudo apt-cache policy docker-ce
sudo apt-get install -y docker-ce
sudo systemctl status docker

now press q to come out this.
ps -ef | grep docker

docker --version

sudo docker run hello-world

the above command should display the below message..

you should see below message 
Hello from Docker!
This message shows that your installation appears to be working correctly.

Setup Docker Registry
Now we need to setup Docker registry. You have one of three options.

Option 1 - DockerHub as Docker Registry
Also, create an account(keep all lowercase in your username)  in the below website for storing docker images in public docker registry..

https://cloud.docker.com/

Option 2 - Configure Nexus as Docker Registry
Please click below link to configure Nexus as Docker Registry.
https://www.cidevops.com/2020/02/how-to-configure-nexus-as-docker.html

Option 3 - Configure AWS ECR as Docker Registry
Please click below link to configure Amazon ECR as Docker Registry.
https://www.cidevops.com/2020/05/how-to-setup-elastic-container-registry.html
 
Option 4 - Configure Azure Container Registry
Please click below link to configure ACR in Azure.
https://www.coachdevops.com/2019/12/how-to-upload-docker-images-to-azure.html

Microservices Introduction
https://www.cidevops.com/2017/01/what-is-microservices-all-about-best.html
Containerization is increasingly popular because containers are:
Flexible: Even the most complex applications can be containerized.
Lightweight: Containers leverage and share the host kernel.
Interchangeable: You can deploy updates and upgrades on-the-fly.
Portable: You can build locally, deploy to the cloud, and run anywhere.
Scalable: You can increase and automatically distribute container replicas.
Stackable: You can stack services vertically and on-the-fly.

Docker Jenkins Integration | Building Docker Images using Jenkins | How to automate Docker Images creation using Jenkins
Every time developer makes code changes, you would want to Jenkins to automate Docker images creation and pushing into Docker registry. Let us see how to do this.

Pre-requisites:
Jenkins is up and running
Docker is installed in Jenkins machine. Click here to learn how to install Docker. 

Docker plug-in installed in Jenkins.
Docker pipeline plug-in installed in Jenkins.

Steps:

Now Login to Jenkins EC2 instance, execute below commands:

Add jenkins user to Docker group
sudo usermod -a -G docker jenkins

Restart Jenkins service
sudo service jenkins restart

Reload system daemon files
sudo systemctl daemon-reload

Restart Docker service as well

sudo service docker stop
sudo service docker start
