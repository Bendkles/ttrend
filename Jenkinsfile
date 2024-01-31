
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
      tools {
        jdk "jdk11"  // Use Java 11 for building
      }
      steps {
        sh 'mvn clean deploy'
      }
    }

    stage('SonarQube analysis') {
      tools {
        jdk "jdk17"  // Use Java 17 for analysis
      }

      environment {
        scannerHome = tool 'sonar-scanner'
      }

      steps {
        withSonarQubeEnv('sonar-scanner') {  // Ensure consistency with tool name
          sh "${scannerHome}/bin/sonar-scanner"
        }
      }
    }
  }
}
