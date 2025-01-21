pipeline {
  agent none
  environment {
    SONARQUBE_TOKEN = credentials('sonarqube')
  }
  tools {
    maven "maven"
  }
  stages {
    stage("Build & Analyse avec SonarQube") {
      agent any
      steps {
        withSonarQubeEnv('sonarqube') {
            sh 'mvn clean verify sonar:sonar -Dsonar.login=${SONARQUBE_TOKEN}'
        }
      }
    }
  }
}
