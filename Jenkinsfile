pipeline {
  agent any
  stages {
    stage('build') {
      parallel {
        stage('build') {
          steps {
            bat 'gradle build'
            archiveArtifacts 'build/libs/*.jar'
          }
        }

        stage('mail') {
          steps {
            mail(subject: 'notification', body: 'sxioiisx', cc: 'ih_merakchi@esi.dz', from: 'in_moulfi@esi.dz')
          }
        }

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
        bat 'gradle publish'
      }
    }

    stage('Slack') {
      steps {
        slackSend(baseUrl: 'https://hooks.slack.com/services/', token: 'T034DQA2M9V/B034WN5H552/9MGoGcswZsLzRIvF8FQ5LmCd', message: 'slack notification')
      }
    }

  }
}
