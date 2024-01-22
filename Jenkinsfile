
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
            tools {
              jdk 'java-11' 
            }
            steps {
                withEnv ( [  'JAVA_HOME=/usr/lib/jvm/java-17-openjdk-amd64',
                'PATH=/usr/lib/jvm/java-17-openjdk-amd64/bin:$PATH'
                          ]) {
                sh 'mvn clean deploy'
            }
        }
    }
}

