pipeline{
  agent any

  stages{
    stage('code ckeckout'){
      steps{
        script{
          git changelog: false, credentialsId: 'd00ba9fc-feb5-46d7-ad17-c08e7a70298d', poll: false, url: 'https://github.com/gkiran04/MyShuttle.git'    
        }
      }
    }

    stage('code analysis'){
      
      steps{
        environment {
          scannerHome = tool 'SonarQubeScanner'
        }
        withSonarQubeEnv(credentialsId: 'sonar') {
          sh '${scannerHome}/bin/sonar-scanner \
          -Dsonar.projectKey=myshuttle \
          -Dsonar.sources=.'
        }
            
        }
    }

  } //stages End

} // Pipeline End