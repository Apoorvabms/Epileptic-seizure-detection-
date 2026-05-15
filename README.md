# Epillepsy-Detection-Using-EEG-signals
Using LSTMs for classification ,whether an EEG signal is Epileptical or not.

# Epilepsy
Epilepsy may occur as a result of a genetic disorder or an acquired brain injury, such as a trauma or stroke.
During a seizure, a person experiences abnormal behaviour, symptoms and sensations, sometimes including loss of consciousness. There are few symptoms between seizures.
Epilepsy is usually treated by medication and in some cases by surgery, devices or dietary changes.

### Seizure
A seizure is a sudden surge of electrical activity in the brain.
A seizure usually affects how a person appears or acts for a short time.
Many different things can occur during a seizure. Whatever the brain and body can do normally can also occur during a seizure.

## Detection 
Epilepsy is the second most common brain disorder after migraine. Automatic detection of epileptic seizures
can considerably improve the patients’ quality of life. CurrentElectroencephalogram (EEG)-based seizure detection systems
encounter many challenges in real-life situations. The EEGs
are non-stationary signals and seizure patterns vary across
patients and recording sessions. Moreover, EEG data are prone to
numerous noise types that negatively affect the detection accuracy
of epileptic seizures. To address these challenges, we introduce the
use of a deep learning-based approach that automatically learns
the discriminative EEG features of epileptic seizures. Specifically,
to reveal the correlation between successive data samples, Long Short-Term Memory (LSTM)
network is used to learn the high-level representations of the normal and the seizure EEG patterns. Secondly, these representations
are fed into Softmax function for training and classification.

## Dataset
**data.csv**
[UCI Machine Repository - Epileptic Seizure Recognition Data Set ](https://archive.ics.uci.edu/ml/datasets/Epileptic+Seizure+Recognition)  
The original dataset from the reference consists of 5 different folders, each with 100 files, with each file representing a single subject/person. Each file is a recording of brain activity for 23.6 seconds. The corresponding time-series is sampled into 4097 data points. Each data point is the value of the EEG recording at a different point in time. So we have total 500 individuals with each has 4097 data points for 23.5 seconds.
We divided and shuffled every 4097 data points into 23 chunks, each chunk contains 178 data points for 1 second, and each data point is the value of the EEG recording at a different point in time. So now we have 23 x 500 = 11500 pieces of information(row), each information contains 178 data points for 1 second(column), the last column represents the label y {1,2,3,4,5}. 
The response variable is y in column 179, the Explanatory variables X1, X2, ..., X178 
y contains the category of the 178-dimensional input vector. Specifically y in {1, 2, 3, 4, 5}: 
5 - eyes open, means when they were recording the EEG signal of the brain the patient had their eyes open  
4 - eyes closed, means when they were recording the EEG signal the patient had their eyes closed  
3 - Yes they identify where the region of the tumor was in the brain and recording the EEG activity from the healthy brain area  
2 - They recorded the EEG from the area where the tumor was located  
1 - Recording of seizure activity  
All subjects falling in classes 2, 3, 4, and 5 are subjects who did not have epileptic seizure. Only subjects in class 1 have epileptic seizure. Our motivation for creating this version of the data was to simplify access to the data via the creation of a .csv version of it. Although there are 5 classes most authors have done binary classification, namely class 1 (Epileptic seizure) against the rest.

## Procedure Followed for Binary Classification 
   Eplileptical - **1**
   Not Epileptical - **0**
1. Model.ipynb :  
    First i visualised the data, for all the 5 classes. 
    (i) Then defined a Recurrent Neural Network architecture , that has 2 layers of LSTMs  
    (ii)Then defined the optimiser as 'adam' and loss as 'binary_crossentropy' which gave better results than 'categorical_crossentropy'  
    (iii)Then I processed the data , by :  
      taking 1 in every 4 samples,then normalising the data and used the previously splitted test data as validation data.  
    (iv) Saved the model after training it for 50 epochs  
    (v) Plotted the rate at which the loss and accuracy are changing.  
2. Product_Final.ipynb  
  The trained model is loaded then its used for prediction on the validation set.
  Now the prediction are changed for binary class, i.e., if the prediction is 1 then the signal is epileptical otherwise the class is made 0 and signal is non epileptical.
  Same procedure is followed for trainig set.


   GitHub Docker Setup Guide
DEVOPS LAB WRITE-UP
**Program – 01**
GitHub – Create an Account and Fork Your
Application Code
Aim
To create a GitHub account and fork an existing repository for independent
development and version control.
Requirements
Internet connection
Web browser
Email account
Procedure
Step 1: Open GitHub Website
1. Open a web browser.
2. Navigate to the GitHub official website: https://github.com
Purpose: GitHub is a cloud-based platform used for hosting and managing
software repositories using Git version control.
Step 2: Create a GitHub Account
1. Click on the “Sign Up” option.
2. Enter the required details:
Username
Complete Devops Lab Writeups Programs 1 To 9
Email address
Password
3. Complete the verification process.
4. Click on “Create Account”.
Purpose: This step creates a personal GitHub account for managing repositories
and collaborating on projects.
Step 3: Verify Email Address
1. Open the registered email inbox.
2. Click on the verification link sent by GitHub.
Purpose: Email verification activates the GitHub account and provides access to
GitHub services.
Step 4: Log in to GitHub
1. Open GitHub.
2. Enter the username and password.
3. Click on “Sign In”.
Purpose: Provides access to the GitHub dashboard and repositories.
Step 5: Search for a Repository
1. Use the search bar available at the top of the GitHub homepage.
2. Enter the repository name.
3. Open the required repository.
Purpose: Allows users to locate public repositories hosted on GitHub.
Step 6: Fork the Repository
1. Click on the “Fork” button available at the top-right corner.
2. Wait for GitHub to create a copy of the repository.
Purpose: Forking creates a personal copy of the original repository in the user’s
GitHub account so changes can be made independently.
Step 7: Verify Forked Repository
1. Open the GitHub profile.
2. Navigate to “Repositories”.
3. Verify that the forked repository is present.
Purpose: Confirms successful forking of the repository.
Result
Thus, a GitHub account was successfully created and the required repository was
forked successfully.
**Program – 02**
To Perform Version Control Operations Using Git and
GitHub
Aim
To perform version control operations using Git and GitHub by managing
repositories and synchronizing changes.
Requirements
Git installed on the system
GitHub account
Internet connection
Procedure
Step 1: Check Git Installation
Open Command Prompt and execute:
Purpose: Checks whether Git is installed and displays the installed version.
Step 2: Configure Git Username and Email
Purpose: Configures the username and email associated with Git commits.
Step 3: Verify Git Configuration
Purpose: Displays all configured Git settings.
Step 4: Create a New Project Directory
Purpose: Creates a directory to store project files.
Step 5: Move to Project Directory
Purpose: Changes the working directory to the project folder.
Step 6: Initialize Git Repository
Purpose: Creates a new Git repository and initializes version tracking.
git --version
git config --global user.name "Varsha"
git config --global user.email "example@gmail.com"
git config --list
mkdir my-project
cd my-project
git init
Step 7: Check Repository Status
Purpose: Displays the current repository status including tracked and untracked
files.
Step 8: Create and Add Files
Purpose: Creates a file and adds it to the staging area.
Step 9: Commit the Changes
Purpose: Saves the staged changes permanently in the repository.
Step 10: View Commit History
Purpose: Displays the history of commits.
Step 11: Create and Switch Branch
Purpose: Creates a new branch and switches to it.
Step 12: Add Feature in Branch
git status
echo "Hello Git" > file.txt
git add file.txt
git commit -m "Initial Commit"
git log
git branch feature-branch
git checkout feature-branch
echo "New Feature" > feature.txt 
Purpose: Adds new changes in the feature branch.
Step 13: Merge Branches
Purpose: Merges the feature branch into the master branch.
Step 14: Connect Local Repository to GitHub
Purpose: Uploads local repository content to GitHub.
Step 15: Clone Repository and Push Changes
Purpose: Creates a local copy of the remote repository.
Result
Thus, version control operations were successfully performed using Git and GitHub.
**Program – 03**
Install Docker and Deploy Containerized Applications
Aim


git add feature.txt
git commit -m "Added feature"
git checkout master
git merge feature-branch
git branch -d feature-branch
git remote add origin https://github.com/username/repository.git
git push -u origin master
git clone https://github.com/username/repository.git
To install Docker, explore Docker commands, create containers using operating
system images, and deploy containerized applications.
Requirements
Docker Desktop
Internet connection
Windows/Linux system
Procedure
Step 1: Download Docker
1. Open browser and visit: https://www.docker.com/products/docker-desktop/
2. Download Docker Desktop.
3. Run the installer.
4. Complete installation and restart the system.
Purpose: Docker Desktop provides the Docker Engine and container runtime
environment.
Step 2: Verify Docker Installation
Purpose: Checks whether Docker is installed successfully.
Step 3: Download Ubuntu Image
Purpose: Downloads the Ubuntu operating system image from Docker Hub.
Step 4: View Docker Images
docker --version
docker pull ubuntu
Purpose: Displays all locally available Docker images.
Step 5: Run Docker Container
Purpose: Creates and starts an Ubuntu container in interactive mode.
Step 6: Execute Commands Inside Container
Purpose: Demonstrates working inside a Docker container.
Step 7: Exit the Container
Purpose: Stops the interactive container session.
Step 8: View Containers
Purpose: Displays running and stopped containers.
Step 9: Start and Stop Containers
docker images
docker run -it ubuntu
apt update
echo "Hello Docker"
exit
docker ps
docker ps -a
docker start <container_id>
Purpose: Manages Docker container lifecycle.
Step 10: Remove Containers and Images
Purpose: Deletes unused containers and images.
Step 11: Deploy Nginx Web Server
Purpose: Deploys an Nginx web server inside a container.
Open browser:
Step 12: Push Image to Docker Hub
Purpose: Uploads Docker images to Docker Hub.
Result
Thus, Docker was successfully installed, containers were created, and containerized
applications were deployed.
**Program – 04**
docker stop <container_id>
docker rm <container_id>
docker rmi ubuntu
docker run -d -p 8080:80 nginx
http://localhost:8080
docker login
docker tag nginx username/nginx-demo
docker push username/nginx-demo
Design, Deploy and Manage Microservices
Architecture using Docker and Docker Compose
Aim
To design, deploy, and manage a microservices architecture using Docker and
Docker Compose.
Requirements
Docker installed
Docker Compose installed
Internet connection
Procedure
Step 1: Verify Docker Installation
Purpose: Checks whether Docker and Docker Compose are installed properly.
Step 2: Create Project Directory
Purpose: Creates a folder for storing project files.
Step 3: Create Application File
Create a file named app.py .
docker --version
docker-compose --version
mkdir microservices-project
cd microservices-project
from flask import Flask 
app = Flask(__name__)
Purpose: Creates a simple microservice application.
Step 4: Create Dockerfile
Purpose: Defines instructions to build a Docker image.
Step 5: Build Docker Image
Purpose: Creates a Docker image from the Dockerfile.
Step 6: Create docker-compose.yml
Purpose: Defines multiple services in a single configuration file.
Step 7: Start Services


@app.route('/')
def home():
 return "Microservice Running"
FROM python:3.10
WORKDIR /app
COPY . .
RUN pip install flask
CMD ["python", "app.py"]
docker build -t microservice-app .
version: '3'
services:
 web:
 build: .
 ports:
 - "5000:5000"
 redis:
 image: redis
Purpose: Starts all services defined in the compose file.
Step 8: Verify Containers
Purpose: Displays running containers.
Step 9: Access the Application
Open browser:
Purpose: Checks whether the application is running successfully.
Step 10: Stop Services
Purpose: Stops all running services.
Step 11: Scale Services
Purpose: Creates multiple instances of the web service.
Result
Thus, a microservices architecture was successfully designed and deployed using
Docker and Docker Compose.
docker-compose up
docker ps
http://localhost:5000
docker-compose down
docker-compose up --scale web=3
**Program – 05**
Install Jenkins and Configure Jenkins for First Use
Aim
To install Jenkins and configure it for first use.
Requirements
Java JDK 21 or above
Windows system
Internet connection
Procedure
Step 1: Download Jenkins
1. Open browser and visit: https://www.jenkins.io/download/
2. Download the Windows MSI installer.
Purpose: Downloads the Jenkins automation server.
Step 2: Run Jenkins Installer
1. Run the jenkins.msi file.
2. Click “Next”.
3. Select installation location.
4. Choose “Run Service as LocalSystem”.
5. Enter port number 8081 .
Purpose: Installs Jenkins as a Windows service.
Step 3: Install Java JDK
1. Download Java JDK 21.
2. Install the JDK.
3. Note the installation path.
Purpose: Jenkins requires Java Runtime Environment.
Step 4: Configure Java Path
1. Browse and select the Java JDK installation folder.
2. Click “Next”.
Purpose: Associates Jenkins with Java.
Step 5: Complete Installation
I’ve prepared the complete write-up for all 9 DevOps lab programs in a proper step-bystep format with aims, requirements, procedures, commands, purposes, and results.




    GitHub Docker Setup Guide
**Program – 06**
Install and Configure SonarQube with Jenkins CI/CD Pipeline
Aim
To install SonarQube and integrate it with Jenkins for performing static code analysis using
a CI/CD pipeline.
Requirements
Jenkins installed
Java JDK installed
Internet connection
SonarQube Server
Procedure
Step 1: Download SonarQube
1. Open a web browser and visit:
https://www.sonarsource.com/products/sonarqube/downloads/
2. Download SonarQube Community Edition.
3. Extract the ZIP file.
Purpose:
Installs SonarQube server used for static code analysis.
Step 2: Start SonarQube Server
Navigate to the following directory:
Run:
Purpose:
Starts the SonarQube server locally.
Step 3: Access SonarQube
sonarqube/bin/windows-x86-64
StartSonar.bat
Open browser:
Login credentials:
Username: admin
Password: admin
Purpose:
Provides access to SonarQube dashboard.
Step 4: Generate SonarQube Token
1. Open Administration → Security.
2. Generate a token.
3. Copy and save the token.
Purpose:
The generated token is used for Jenkins authentication.
Step 5: Install SonarQube Scanner Plugin in Jenkins
1. Open Jenkins Dashboard.
2. Navigate to:
Manage Jenkins → Plugins
3. Search for “SonarQube Scanner”.
4. Install the plugin.
Purpose:
Enables Jenkins integration with SonarQube.
Step 6: Configure SonarQube in Jenkins
1. Open:
Manage Jenkins → System
2. Add SonarQube server.
3. Enter:
Name: sonar
URL: http://localhost:9000
4. Add secret text credentials using generated token.
5. Save configuration.
Purpose:
Connects Jenkins with SonarQube server.
http://localhost:9000
Step 7: Configure SonarQube Scanner Tool
1. Open:
Manage Jenkins → Tools
2. Add SonarQube Scanner installation.
3. Name it “sonar”.
Purpose:
Allows Jenkins pipelines to use SonarQube scanner.
Step 8: Create Jenkins Pipeline
1. Create a new Pipeline project.
2. Add the following pipeline script:
Purpose:
Performs automated static code analysis using SonarQube.
Step 9: Run the Pipeline
1. Click “Build Now”.
2. Monitor console output.
3. Open SonarQube dashboard and verify analysis report.
Purpose:
Executes the CI/CD pipeline successfully.
Result
Thus, SonarQube was successfully integrated with Jenkins and static code analysis was
performed successfully.
pipeline {
agent any
stages {
 stage('Code Analysis') {
 steps {
 withSonarQubeEnv('sonar') {
 bat 'sonar-scanner'
 }
 }
 }
}
}
groovy
**Program – 07**
Demonstrate Fundamentals of Maven and Gradle
Aim
To demonstrate the fundamentals of Maven and Gradle build automation tools.
Requirements
Java JDK installed
Maven installed
Gradle installed
Internet connection
Procedure
Step 1: Install Java JDK
1. Download and install Java JDK.
2. Verify installation:
Purpose:
Java is required for Maven and Gradle execution.
Step 2: Install Maven
1. Download Maven from:
https://maven.apache.org/download.cgi
2. Extract ZIP file.
3. Configure environment variables.
Verify installation:
Purpose:
Maven is used for build automation and dependency management.
Step 3: Install Gradle
java -version
mvn -v
Bash
Bash
1. Download Gradle from:
https://gradle.org/releases/
2. Extract ZIP file.
3. Configure environment variables.
Verify installation:
Purpose:
Gradle is an advanced build automation tool.
Step 4: Understand Maven Structure
Important Maven files:
pom.xml
src/main/java
src/test/java
Purpose:
Maven uses XML configuration for project management.
Step 5: Understand Gradle Structure
Important Gradle files:
build.gradle
settings.gradle
Purpose:
Gradle uses Groovy/Kotlin DSL configuration.
Step 6: Execute Maven Commands
gradle -v
mvn compile
mvn test
mvn package
Bash
Bash
Bash
Bash
Purpose:
Compiles, tests, and packages the Maven application.
Step 7: Execute Gradle Commands
Purpose:
Builds and tests applications using Gradle.
Step 8: Compare Maven and Gradle
Maven uses XML-based configuration.
Gradle uses Groovy/Kotlin DSL.
Gradle supports incremental builds.
Maven provides standard project structure.
Purpose:
Helps understand differences and advantages of both tools.
Result
Thus, the fundamentals of Maven and Gradle were successfully demonstrated.
**Program – 08**
Create a Maven Project and Understand POM File, Dependency
Management and Plugins
Aim
To create a Maven project and understand the POM file, dependency management, and
plugins.
Requirements
Java JDK installed
Maven installed
gradle build
gradle test
Bash
Bash
Procedure
Step 1: Verify Maven Installation
Purpose:
Checks whether Maven is installed properly.
Step 2: Create Maven Project
Purpose:
Creates a Maven project using quickstart archetype.
Step 3: Navigate to Project Folder
Purpose:
Moves to the project directory.
Step 4: Understand POM File
Open pom.xml .
Important sections:
groupId
artifactId
version
dependencies
plugins
Purpose:
The POM file stores project configuration and dependencies.
mvn -v
 
mvn archetype:generate -DgroupId=com.example -DartifactId=demo-project -DarchetypeArtifactId
cd demo-project
Bash
Bash
Bash
Step 5: Add Dependency
Add Gson dependency inside <dependencies> section.
Purpose:
Adds external libraries to the project.
Step 6: Compile the Project
Purpose:
Compiles the source code.
Step 7: Run Unit Tests
Purpose:
Executes test cases.
Step 8: Package the Project
Purpose:
Creates JAR file for the application.
Step 9: Execute the JAR File
<dependency>
 <groupId>com.google.code.gson</groupId>
 <artifactId>gson</artifactId>
 <version>2.10.1</version>
</dependency>
mvn compile
mvn test
mvn package
XML
Bash
Bash
Bash
Bash
Purpose:
Runs the Maven application.
Result
Thus, a Maven project was successfully created and the POM file, dependency
management, and plugins were understood successfully.
**Program – 09**
Build and Run Java Application with Maven and Migrate the Same
Application to Gradle
Aim
To build and run a Java application using Maven and migrate the same application to
Gradle.
Requirements
Java JDK installed
Maven installed
Gradle installed
Part A – Build and Run Java Application using Maven
Procedure
Step 1: Verify Java Installation
Purpose:
Checks whether Java is installed successfully.
Step 2: Verify Maven Installation
java -cp target/demo-project-1.0-SNAPSHOT.jar com.example.App
java -version
mvn -v
Bash
Bash
Purpose:
Checks Maven installation.
Step 3: Create Maven Project
Purpose:
Creates a Maven Java project.
Step 4: Add Dependency in pom.xml
Purpose:
Adds Gson library dependency.
Step 5: Build Maven Project
Purpose:
Compiles, tests, and packages the application.
Step 6: Run the Application
 
mvn archetype:generate -DgroupId=com.example -DartifactId=demo-project -DarchetypeArtifactId
<dependency>
 <groupId>com.google.code.gson</groupId>
 <artifactId>gson</artifactId>
 <version>2.10.1</version>
</dependency>
mvn compile
mvn test
mvn package
Bash
XML
Bash
Bash
Bash
Purpose:
Executes the Maven application.
Part B – Migrate Application to Gradle
Step 7: Delete Maven-Specific Files
Delete:
pom.xml
Do not delete the src folder.
Purpose:
Removes Maven configuration while retaining application source code.
Step 8: Create build.gradle
Purpose:
Defines Gradle project configuration.
Step 9: Create settings.gradle
java -cp target/demo-project-1.0-SNAPSHOT.jar com.example.App
plugins {
id 'java'
}
group = 'com.example'
version = '1.0-SNAPSHOT'
repositories {
mavenCentral()
}
dependencies {
testImplementation 'junit:junit:4.13.2'
}
rootProject.name = 'demo-project'
Bash
gradle
gradle
Do you like this personality?
Purpose:
Defines project name.
Step 10: Build Gradle Project
Purpose:
Builds and tests the application using Gradle.
Step 11: Run Gradle Application
Purpose:
Runs the Gradle application.
Result
Thus, the Java application was successfully built and executed using Maven and migrated
successfully to Gradle.
gradle build
gradle test
java -cp build/libs/demo-project-1.0-SNAPSHOT.jar com.example.App
Bash
Bash
Bash
