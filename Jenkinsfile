
pipeline {
    agent {
        node {
            label 'maven'
        }
    }
    
    environment {
        PATH = "/opt/apache-maven-3.9.6/bin:$PATH"
        JAVA_HOME = '/usr/lib/jvm/java-17-openjdk-amd64'
    }
    
    stages {
        stage("build") {
            tools {
                jdk 'java-11'
            }
            steps {
                sh 'mvn clean deploy'
            }
        }
    }
}
