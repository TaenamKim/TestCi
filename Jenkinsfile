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
sudo mkdir -p ../release/onnara-mobile
sudo find . -name \\*.apk -exec cp {} ../release/onnara-mobile \\;'''
      }
    }
  }
}