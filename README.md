# djangoNotesApp

#Docker&Jenkins
sudo apt-get update
sudo apt install docker.io
docker --version
docker ps
whoami
sudo usermod -aG docker ubuntu
sudo reboot

git clone django-notes
cd django-notes
ls
cat DockerFile
docker build -t notesapp:1.0 .
docker image ls

sudo apt install openjdk-17-jre
java -version

curl -fsSL https://pkg.jenkins.io/debian/jenkins.io-2023.key | sudo tee \
  /usr/share/keyrings/jenkins-keyring.asc > /dev/null
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
  https://pkg.jenkins.io/debian binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt-get update

sudo apt-get install jenkins
service jenkins status
sudo usermod -aG docker ubuntu
sudo apt install docker-compose
docker-compose --version

ManageJenkins-
Credentials-dockerhub[Username&Password],sonarsecret[secretkey]
System[Global Settings]-Add sonar-server[Pass name,url & sonarsecret configure earlier]
Tools[Configure Tool]-Add SonarQubeScanner

#Github
generate private & public key for ssh connection in local machine
add public key to your github account

eval `ssh-agent -s`
ssh add key 
ssh -T git@github.com

#ChangeHostname
sudo hostnamectl set-hostname jenkins
/bin/bash

#SonarQube[Work in sonar user not in ububtu user]
apt install unzip
adduser sonarqube
wget https://binaries.sonarsource.com/Distribution/sonarqube/sonarqube-9.4.0.54424.zip
unzip *
chmod -R 755 /home/sonarqube/sonarqube-9.4.0.54424
chown -R sonarqube:sonarqube /home/sonarqube/sonarqube-9.4.0.54424
cd sonarqube-9.4.0.54424/bin/linux-x86-64/
./sonar.sh start


--Create a manual project in sonar
--Pass project-id & project-key details
--Select tool jenkins to analyze code

--Create sonarsecret from profile 

#linux-command
pwd
cd
ls
su-[switchuser]
cat
vi 
nano [editor]
chmod [Manage permission/control over a directory]
chown user:group directorypath [change/transfer permission to other user over a directory]
adduser
apt install
rm -r
apt autoremove
usermod -aG 
hostnamectl set-hostname name  /bin/bash
touch [create an empty file]
df [disk usage info]
du [calc size of directory]
who [users logged in server/system]
whoami [username]

#minikube info
 minikube start
* minikube v1.32.0 on Microsoft Windows 11 Pro 10.0.22631.2861 Build 22631.2861
* Automatically selected the docker driver
* Using Docker Desktop driver with root privileges
* Starting control plane node minikube in cluster minikube
* Pulling base image ...
* Downloading Kubernetes v1.28.3 preload ...
    > gcr.io/k8s-minikube/kicbase...:  453.90 MiB / 453.90 MiB  100.00% 2.13 Mi
* Creating docker container (CPUs=2, Memory=5000MB) ...
! Executing "docker ps -a --format {{.Names}}" took an unusually long time: 3.2371818s
* Restarting the docker service may improve performance.
* Preparing Kubernetes v1.28.3 on Docker 24.0.7 ...
  - Generating certificates and keys ...
  - Booting up control plane ...
  - Configuring RBAC rules ...
* Configuring bridge CNI (Container Networking Interface) ...
* Verifying Kubernetes components...
  - Using image gcr.io/k8s-minikube/storage-provisioner:v5
* Enabled addons: storage-provisioner, default-storageclass

! C:\Program Files\Docker\Docker\resources\bin\kubectl.exe is version 1.25.4, which may have incompatibilities with Kubernetes 1.28.3.
  - Want kubectl v1.28.3? Try 'minikube kubectl -- get pods -A'
* Done! kubectl is now configured to use "minikube" cluster and "default" namespace by default


