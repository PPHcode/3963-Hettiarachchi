pipeline {
    agent any
    stages {
        stage ('Checkout'){
            steps{
                retry(3){
                  checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/PPHcode/3963-Hettiarachchi/']])
                }
            }
      
        }
        stage('build dockerfile'){
            steps {
                sh 'docker build -t piyumidoc/3963-my_docker_file .'
            }
        
        }
        stage('Dockerfile run') {
            steps {
                script {
                    def output = sh(script: 'docker run -d -p 3000 piyumidoc/3963-my_docker_file', returnStdout: true).trim()
                    echo "Container started with ID: $output"
                }
            }
        }
       
        
        stage('show running containers'){
      steps{
        sh 'docker ps'
      }
    }
    
    }
}