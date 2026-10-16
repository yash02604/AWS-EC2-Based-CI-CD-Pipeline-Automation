# Spring PetClinic CI/CD Pipeline

## Project Overview

This project demonstrates the automation of the software build, code analysis, artifact management, and deployment lifecycle using Jenkins and DevOps tools.

The pipeline builds and tests the Spring PetClinic application, analyzes code quality with SonarQube, publishes the WAR artifact to Nexus Repository Manager, and deploys the application to Apache Tomcat hosted on AWS EC2.

## Technologies Used

- **Cloud:** AWS EC2
- **CI/CD:** Jenkins
- **Version Control:** Git and GitHub
- **Build Automation:** Maven
- **Code Quality:** SonarQube
- **Artifact Management:** Nexus Repository Manager
- **Application Server:** Apache Tomcat
- **Operating System:** Linux
- **Remote Deployment:** SSH and SCP

## CI/CD Workflow

1. **Git Checkout:** Jenkins retrieves source code from GitHub.
2. **Build and Test:** Maven compiles the application, runs automated tests, and packages the WAR file.
3. **Code Analysis:** SonarQube performs static code analysis.
4. **Artifact Upload:** Nexus stores the generated WAR artifact.
5. **Deployment:** Jenkins transfers the WAR file to the Tomcat server on AWS EC2.

## Validation Results

- All five Jenkins pipeline stages completed successfully in a verified build.
- Maven executed 62 tests with zero failures or errors.
- The WAR artifact was uploaded to Nexus Repository Manager.
- The application was accessible through the Tomcat server.

## Key Learning Outcomes

- Jenkins pipeline configuration and stage orchestration
- Maven build and test automation
- SonarQube integration for code quality analysis
- Nexus artifact repository integration
- AWS EC2-based application hosting
- SSH/SCP-based remote deployment

## Source Application

Spring PetClinic: https://github.com/spring-projects/spring-petclinic

## Security

Credentials, private SSH keys, access tokens, passwords, and sensitive environment configuration are maintained outside the repository.
