def imageName = 'ashishp1.jfrog.io/artifactory/default-docker-local/ashish-rtp'
def registry  = 'https://ashishp1.jfrog.io'
def app
pipeline {
    agent {
       node {
         label "valaxy"
      }
    }
    stages {
        stage('Build') {
            steps {
                echo '<--------------- Building --------------->'
                sh 'printenv'
                sh 'mvn clean deploy -Dmaven.test.skip=true'
                echo '<------------- Build completed --------------->'
            }
        }
      stage('Sonar Analysis') {
            environment {
                scannerHome = tool 'SonarQubeScanner'
            }
            steps {
                echo '<--------------- Sonar Analysis Started --------------->'
                withSonarQubeEnv('SonarQube'){
                    sh "${scannerHome}/bin/sonar-scanner"
                }    
                echo '<--------------- Sonar Analysis Ends --------------->'
            }    
        } 
    }
 }
