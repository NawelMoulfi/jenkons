pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        bat 'gradle build'
        archiveArtifacts 'build/libs/*.jar'
      }
    }

    stage('test') {
      steps {
        bat 'gradle test'
      }
    }

    stage('documentation') {
      steps {
        bat 'gradle javadoc'
      }
    }


    stage('deploy') {
      steps {
        bat 'gradle jar'
      }
    }

    stage('Slack') {
      steps {
        slackSend(baseUrl: 'https://hooks.slack.com/services/', token: 'T034DQA2M9V/B034WN5H552/9MGoGcswZsLzRIvF8FQ5LmCd', message: 'slack notification')
      }
    }

  }
}
