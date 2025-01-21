pipeline {
  agent none
  environement {
    SONARQUBE_TOKEN = credentials('sonarqube')
  }
  tools {
    maven "maven"
  }
  stages {
    stage("Build & Analyse avec SonarQube") {
      agent any
      steps {
        withSonarQubeEnv('SonarQube') {
            sh 'mvn clean verify sonar:sonar -Dsonar.login=${SONARQUBE_TOKEN}'
        }
      }
    }
  }
}
