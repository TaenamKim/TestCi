pipeline {
  agent any
  stages {
    stage('cleanBuild') {
      steps {
        sh '''chmod 777 gradlew 
./gradlew clean build --stacktrace'''
      }
    }
    stage('PostBuild') {
      steps {
        sh 'ls -alF /data/jenkins-android-docker/workspace/TestCi_master/app/build/outputs/apk'
      }
    }
  }
}