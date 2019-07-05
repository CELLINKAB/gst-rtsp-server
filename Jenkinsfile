pipeline {
  agent any
  stages {
    stage('Git Fectch Repo') {
      parallel {
        stage('Git Fectch Repo') {
          steps {
            git(url: 'https://github.com/CELLINKAB/CellCyteX-Backend-API.git', changelog: true, credentialsId: 'GitHubToken', poll: true)
          }
        }
        stage('Slack Notification') {
          steps {
            slackSend(channel: 'cloud', token: 'TXPXiLbn6oz4WmL6fWAF3EEt', username: 'jenkins', teamDomain: 'cellink-sw', message: 'Git Repo Fetch Successfull', tokenCredentialId: 'SlackToken', color: 'good', sendAsText: true)
          }
        }
      }
    }
    stage('Build and Execute Unit Tests') {
      steps {
        sh 'pytest -v  --slack_hook=https://hooks.slack.com/services/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 --slack_channel=deployment-noise --slack_username="Regression testing results"'
      }
    }
  }
}