
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
            environment {
                mavenHome = tool 'maven-3.9.6-java-11' // Use Java 11 for Maven build
            }
            steps {
                sh 'mvn clean deploy'
            }
        }

        stage('SonarQube analysis') {
            environment {
                JAVA_HOME = "/usr/lib/jvm/java-17-openjdk-amd64" // Use Java 17 for SonarQube
            }
            steps {
                withEnv(overrides: [
                    JAVA_HOME: "/usr/lib/jvm/java-17-openjdk-amd64" // Ensure Java 17 is used within the block
                ]) {
                    sh "${scannerHome}/bin/sonar-scanner"
                }
            }
        }
    }
}
