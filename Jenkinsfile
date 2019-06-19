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
      parallel {
        stage('PostBuild') {
          steps {
            sh '''pwd
ls -alF ./app/build/outputs/apk
mkdir -p ../release/onnara-mobile
find . -name \\*.apk
find . -name \\*.apk -exec cp {} ../release/onnara-mobile \\;'''
          }
        }
        stage('PostMsg') {
          steps {
            slackSend(baseUrl: 'https://urpsystem.slack.com/messages/CKR53CUTZ/whats_new/', channel: 'test-mobile-result', failOnError: true, token: 'qvqwJOg6ElnGvIpZkjnbyWQE', message: 'HI', attachments: '{}', color: '#4962ad', teamDomain: 'https://urpsystem.slack.com', tokenCredentialId: 'WlpkYUuxY61jq7BxGoVS2r9C')
          }
        }
      }
    }
  }
}