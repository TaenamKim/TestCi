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
        sh '''pwd
ls -alF ./app/build/outputs/apk
mkdir -p ../release/onnara-mobile
find . -name \\*.apk
find . -name \\*.apk -exec cp {} /data/jenkins-android-docker/release/onnara-mobile \\;'''
      }
    }
  }
}