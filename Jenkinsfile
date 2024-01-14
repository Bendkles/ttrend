

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

        stage('SCM') {
            steps {
                script {
                    git credentialsId: 'Github-Cred', url: 'https://github.com/foo/bar.git'
                }
            }    
        }
        
        stage('SonarQube analysis') {
            environment {
                scannerHome = tool 'sonarqube-scanner'
            }
            steps {
                withSonarQubeEnv('sonarqube-svr') { // If you have configured more than one global server connection, you can specify its name
                    sh "${scannerHome}/bin/sonar-scanner"
                }
            }   
        }
    }
}  
