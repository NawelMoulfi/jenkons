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
      parallel {
        stage('documentation') {
          steps {
            bat 'gradle javadoc'
          }
        }

         stage('Cucumber') {
          steps {
            cucumber(fileIncludePattern: '**/Cucumber.json', buildStatus: 'Unstable', jsonReportDirectory: 'C:\\Users\\Lenovo\\Desktop\\Nawel')
          }
        }

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
