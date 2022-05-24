pipeline {
  agent any
  stages {
    stage('clone repository') {
      steps {
        sh '''java -version
mvn --version
git --version'''
      }
    }

    stage('Deploy billing App') {
      steps {
        withCredentials(bindings: [
                      string(credentialsId: 'kubernete-jenkis-server-account', variable: 'api_token')
                      ]) {
            sh 'kubectl --token $api_token --server https://10.203.230.197:8443 --insecure-skip-tls-verify=true apply -f deployment-billing-app-back-jenkins.yaml '
          }

        }
      }

    }
  }
