
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
        stage("build") {
            steps {
                sh 'mvn clean deploy'
            }
        }

        stage('SonarQube analysis') {
            environment {
                scannerHome = tool 'sonar-scanner'
                mavenHome = tool 'maven-3.9.6-java-17'
                JAVA_HOME = "/opt/apache-maven-3.9.6/jre"
            }
            steps {
                sh "echo $JAVA_HOME"  // Print JAVA_HOME value
                withSonarQubeEnv('sonarqube-server') {
                    sh "${scannerHome}/bin/sonar-scanner"
                }
            }
        }
    }
}
