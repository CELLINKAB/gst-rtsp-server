pipeline {
  agent any
  stages {
    stage('Slack Notification') {
      steps {
        slackSend(channel: 'deployment-noise', token: 'TXPXiLbn6oz4WmL6fWAF3EEt', username: 'jenkins', teamDomain: 'cellink-sw', message: 'CellCyteX-Backend-API :Pipeline Starting', tokenCredentialId: 'SlackToken', color: 'good', sendAsText: true)
      }
    }
    stage('Fetch Latest Code') {
      steps {
        git(url: 'https://github.com/CELLINKAB/CellCyteX-Backend-API.git', changelog: true, credentialsId: 'GitCred', poll: true)
      }
    }
    stage('Fetch Latest Code Complete') {
      steps {
        slackSend(channel: 'deployment-noise', token: 'TXPXiLbn6oz4WmL6fWAF3EEt', username: 'jenkins', teamDomain: 'cellink-sw', message: 'CellCyteX-Backend-API :Fetch from Git Repo Completed', tokenCredentialId: 'SlackToken', color: 'good', sendAsText: true)
      }
    }
    stage('Build and Run Code Tests') {
      steps {
        pysh(script: './runTests.sh', returnStatus: true, returnStdout: true)
      }
    }
  }
}