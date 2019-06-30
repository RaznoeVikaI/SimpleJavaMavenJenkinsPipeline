pipeline {
       agent any
       tools {
               maven 'myMaven'
           }
       stages{

              stage('Build') {
                   steps {
                            sh 'mvn -B -U surefire:test -DtestFailureIgnore=true'
                   }
              }
              stage('Clean'){
                    steps{
                        sh 'mvn clean'
                    }
              }
              stage('Test') {
                steps{
                        sh 'mvn test'
                }
              }
       }
       post {
          always {
                      archive "target/**/*"
                      junit 'target/surefire-reports/*.xml'
                  }
       }
}