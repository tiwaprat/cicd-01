In this project we will setup Jenkins on EC2 and integrate it with GitHub repo. We also create a simple job that clones repo to Jenkins workspace 


Step 1: Lets provision a Linux 2 based ec2 instance. 
step follow this doc to install Jenkins on ec2. 

https://www.jenkins.io/doc/tutorials/tutorial-for-installing-jenkins-on-AWS/#downloading-and-installing-jenkins
These are the commands 
     sudo yum upgrade
     sudo yum install java-17-amazon-corretto -y
     sudo wget -O /etc/yum.repos.d/jenkins.repo \
    https://pkg.jenkins.io/redhat-stable/jenkins.repo
     sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io-2023.key
     sudo yum install jenkins -y
     sudo systemctl enable jenkins
     sudo systemctl start jenkins
     sudo systemctl status jenkins      

step2: Open port 8080 and login to Jenkins. Setup user and password. 
step3: Lets configure Jenkins for git repo. 
    1. First create a brand new repo cicd-01 in GitHub for simplicity I have created public repo. 
    2. create add a simple file test.txt to GitHub repo just to check connectivity. 
    3. Login to jenkin and install GitHub Integration Plugin.
    4. Install git on Jenkins server this required to run git commands to pull code from GitHub. 
        sudo yum update 
        sudo yum install git -y 
        git --version
    5. login to Jenkins and install GitHub plugin 
    6. Login to Jenkins -> create a job name PullCodeFromJenkins -> project type freestyle-> Description "This job will only pull code from github to Jenkins workspace." -> SCM git -> Repo url "https://github.com/tiwaprat/cicd-01.git" -> 
    7. Cross verify if name of branches matched in Jenkins configuration and GitHub repo. 
    8. Build now in jenkns 
    9. Verify on ec2 Jenkins server if code got copied into work space. 


This demonstrate a simple integration of Jenkins and GitHub SCM  







