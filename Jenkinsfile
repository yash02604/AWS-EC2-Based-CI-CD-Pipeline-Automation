pipeline {
    agent any

    stages {
        stage('git-clone') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/yash02604/Spring-PetClinic-CICD-Pipeline.git'
            }
        }

        stage('package') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('sonarqube') {
            steps {
                withSonarQubeEnv(
                    installationName: 'SonarQube',
                    credentialsId: 'jenkins-sonar'
                ) {
                    sh 'mvn clean verify org.sonarsource.scanner.maven:sonar-maven-plugin:sonar'
                }
            }
        }
        stage ('nexus'){
            steps{
                nexusArtifactUploader artifacts: [[artifactId: 'spring-framework-petclinic',
                classifier: '',
                file: 'target/petclinic.war',
                type: 'war']],
                credentialsId: 'nexus',
                groupId: 'org.springframework.samples',
                nexusUrl: '52.66.16.75:8081',
                nexusVersion: 'nexus3',
                protocol: 'http',
                repository: 'spring-petclinic', 
                version: '6.2.8'
            }
        }
        stage('Deploy to Tomcat') {
            steps {
                sshagent(credentials: ['tomcat']) {
                    sh '''
                        ssh -o StrictHostKeyChecking=no \
                            ubuntu@65.2.148.205 "whoami"

                        scp -o StrictHostKeyChecking=no \
                            target/petclinic.war \
                            ubuntu@65.2.148.205:/home/ubuntu/apache-tomcat-10.1.61/webapps/
                    '''
                }
            }
        }
    }
}
