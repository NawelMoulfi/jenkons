pipeline {
agent any
 
stages {
     stage ('build') { // la phase build
           steps { // les étapes de la phase build......... // les instructions à exécuter
                  bat 'gradle build'
                  archiveArtifacts 'build/libs/*.jar'
                  }
                       }
      stage ('test') { // la phase test
          steps {
             bat 'gradle test'
               }
                    }
  
      stage ('deploy') { // la phase deployement
      steps {
          bat 'gradle jar'
          }
              }
               }
                  }
