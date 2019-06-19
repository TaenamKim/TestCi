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
            slackSend(baseUrl: 'https://urpsystem.slack.com/services/hooks/jenkins-ci/', channel: 'test-mobile-result', failOnError: true, token: 'qvqwJOg6ElnGvIpZkjnbyWQE', message: 'HI', attachments: '{             "fallback": "Required plain-text summary of the attachment.",             "color": "#36a64f",             "pretext": "Optional text that appears above the attachment block",             "author_name": "Bobby Tables",             "author_link": "http://flickr.com/bobby/",             "author_icon": "http://flickr.com/icons/bobby.jpg",             "title": "Slack API Documentation",             "title_link": "https://api.slack.com/",             "text": "Optional text that appears within the attachment",             "fields": [                 {                     "title": "Priority",                     "value": "High",                     "short": false                 }             ],             "image_url": "http://my-website.com/path/to/image.jpg",             "thumb_url": "http://example.com/path/to/thumb.png",             "footer": "Slack API",             "footer_icon": "https://platform.slack-edge.com/img/default_application_icon.png",             "ts": 123456789         }', color: '#4962ad', teamDomain: 'https://urpsystem.slack.com', botUser: true, tokenCredentialId: 'WlpkYUuxY61jq7BxGoVS2r9C')
          }
        }
      }
    }
  }
}