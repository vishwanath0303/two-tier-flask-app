pipeline {
    agent any 
    
    stages{
        stage("Clone Code"){
            steps {
                echo "Cloning the code"
                git url:"https://github.com/vishwanath0303/two-tier-flask-app", branch: "master" 
            }
        }
        stage("Build and creating container"){
            steps {
                echo "Building the image"
                sh "docker build -t two-tier-flask-app:$BUILD_NUMBER ."
            }
        }
        stage("Deploy"){
            steps {
                echo "Deploying the container"
                sh "docker-compose down && docker-compose up -d"
                
            }
        }
     }
 }
