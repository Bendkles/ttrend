
pipeline {
    agent {
        node {
            label 'maven'
        }
    }

    environment {
        PATH = "/opt/apache-maven-3.9.6/bin:$PATH"
    }

    stages {
        stage("build"){
            steps {
                sh 'mvn clean deploy'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                script {
                    def mvnHome = tool 'Maven';
                    withSonarQubeEnv() {
                        sh "${mvnHome}/bin/mvn clean verify sonar:sonar -Dsonar.projectKey=devopsproject-2-key -Dsonar.projectName='devops-project-2'"
                    }
                }
            }
        }
    }
}

