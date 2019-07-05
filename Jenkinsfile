pipeline {
  agent any
  stages {
    stage('Slack Notification') {
      steps {
        slackSend(channel: 'cloud', token: 'TXPXiLbn6oz4WmL6fWAF3EEt', username: 'jenkins', teamDomain: 'cellink-sw', message: 'CellCyteX-Backend-API :Pipeline Starting', tokenCredentialId: 'SlackToken', color: 'good', sendAsText: true)
      }
    }
    stage('Fetch Latest Code') {
      steps {
        git(url: 'https://github.com/CELLINKAB/CellCyteX-Backend-API.git', changelog: true, credentialsId: 'GitHubToken', poll: true)
      }
    }
  }
}