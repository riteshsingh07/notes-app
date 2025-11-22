# Simple Notes App
This is a simple notes app built with React and Django.

## Requirements
1. Python 3.9
2. Node.js
3. React

## Installation
1. Clone the repository
```
git clone https://github.com/riteshsingh07/notes-app.git
```

2. Build the app
```
docker build -t notes-app .
```

3. Run the app
```
docker run -d -p 8000:8000 notes-app:latest
```

## EC2 Instance 
1. Create 2 ec2 instances
   a. MasterCICD : for connecting to master jenkin.
   b. AgentCICD : Jenkins works on Master-Agent architecture, all the work are done under Agent.

## Jenkins Installation
SSH MasterCICD instance, install Java and jenkins.

```
sudo apt update
sudo apt install fontconfig openjdk-21-jre
java -version
```

Jenkins : Long Term Support release

```
sudo wget -O /etc/apt/keyrings/jenkins-keyring.asc \
  https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key
echo "deb [signed-by=/etc/apt/keyrings/jenkins-keyring.asc]" \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt update
sudo apt install jenkins
```

Note : No need of Jenkin installation is required on AgentCICD instance, only Java will be enough.

## Jenkins connecting Master with Agent

1. Create private and public key on MasterCICD instance.
```
cd ~/.ssh
ssh-keygen
```
2. Paste the public key in the authorized_keys file.
```
cd ~/.ssh
vim authorized_keys
```
3. While creating an Agent on jenkins. Paste the private key for SSH and public ip of AgentCICD.

## Jenkins Pipeline Code

Create a Item with Declarative Pipeline
