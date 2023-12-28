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
