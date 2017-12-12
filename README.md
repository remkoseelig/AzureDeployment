# Azure Deployment
Demo project that creates a VM in Azure and deploys a simple web application.

## 1. Setup Jenkins

If you already have a Jenkins server running, go to step 2. 

Otherwise, you can simple install Docker and run Jenkins locally. Run the code below to start Jenkins. The '-v' option mounts a local folder to the Docker container so that all important Jenkins files are stored for subsequent runs. 

### Start Jenkins

Windows

`docker run -v "%USERPROFILE%\Jenkins":/var/jenkins_home -p 8080:8080 --name Jenkins -d jenkins/jenkins:lts`

Linux

`docker run -v $HOME/jenkins:/var/jenkins_home -p 8080:8080 --name Jenkins -d jenkins/jenkins:lts`

### Configure Jenkins for first run

The first time Jenkins is started, it asks you to provide the initial admin password Jenkins generated. It's located in the Docker container itself, so you need to open it. The line below instructs Docker to output the contents of that file in the running container.

`docker exec Jenkins cat /var/jenkins_home/secrets/initialAdminPassword`

## 2. Create pipeline

Create an empty pipeline.
