pipeline {
    agent any 
    
    stages{
        stage("Clone Code"){
            steps {
                echo "Cloning the code"
                git url:"https://github.com/vishwanath0303/two-tier-flask-app", branch: "master" 
            }
        }
        stage("Build"){
            steps {
                echo "Building the image"
                sh "docker build -t two-tier-flask-app:$BUILD_NUMBER ."
            }
        }
          stage ("Stop and remove") {
           steps {
             script{
               sh 'docker ps -a -q'
               sh 'docker stop two-tier-flask-app '
               sh 'docker rm two-tier-flask-app '
             }
           }
        }
        stage('Start image'){
            steps{
                script{
                    sh 'docker run -d -p 8181:8181 --name two-tier-flask-app two-tier-flask-app:$BUILD_NUMBER '
                }
            }
         }  
     }
 }
