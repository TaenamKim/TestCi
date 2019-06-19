pipeline {
  agent any
  stages {
    stage('CleanBuild') {
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
find . -name \\*.apk -exec cp {} /var/jenkins_home/release/onnara-mobile \\;'''
      }
    }
  }
}