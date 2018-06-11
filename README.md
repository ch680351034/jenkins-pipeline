# Jenkins Pipeline for CI/CD
## Prerequisites
* [Jenkins](https://jenkins.io/download/) 
* [docker](https://docs.docker.com/) 
* [docker-compose](https://docs.docker.com/compose/install/)

##  Getting Started
* Download and install Jenkins. 
* In Jenkins, make sure to install docker and docker-compose.

### Jenkins Pipeline
* From the Jenkin's Dashboard, select New Item. 
  * Enter an Item Name and select Pipeline
  * Select OK

  ![New Item](images/jenkins-new-item.jpg)

* From the Jenkin's Dashboard, select New Item. 
  * Enter an Item Name and select Pipeline
  * Click OK
* Click on the Pipeline Tab 
  * Definition: Pipeline script from SCM
  * SCM: Git
  * Repositories:  Input the repository URL and credentials [select None if it's a public repository]
  * Branches to build: For this example, I used */master. You can also create a parameterized project.
  * Script Path: Jenkinsfile
* Click SAVE.

  ![Pipeline SCM](images/jenkins-pipeline-scm.jpg)

#### Jenkins Pipeline Stage View

  ![Stage View](images/jenkins-stage-view.jpg)

#### Jenkins Pipeline Approval Stage

  ![Approval](images/jenkins-approval.jpg)

 
