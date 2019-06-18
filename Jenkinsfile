pipeline {
  agent any
  stages {
    stage('cleanBuild') {
      steps {
        sh '''sudo chmod 777 gradlew 
./gradlew clean build --stacktrace'''
      }
    }
  }
}