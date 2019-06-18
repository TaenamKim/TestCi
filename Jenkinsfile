pipeline {
  agent any
  stages {
    stage('cleanBuild') {
      steps {
        sh './gradlew clean build --stacktrace'
      }
    }
  }
}