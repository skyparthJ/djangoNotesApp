pipeline {
    agent any
    environment{
        SONAR_HOME= tool "sonarscanner"
    }
    
    stages {
        stage("code") {
            steps {
                //git url:"https://github.com/skyparthJ/djangoNotesApp.git",branch:"main"
                echo "clone an image"
            }
        }
        stage("SonarQube Analysis"){
            steps{
                withSonarQubeEnv(){
                    sh "$SONAR_HOME/bin/sonar-scanner -Dsonar.projectName=jenkins -Dsonar.projectKey=jenkins"
                }
            }
        }
        stage("image-build"){
            steps{
                sh "docker build -t appnotes:1.0 ."
                echo "build an image"
            }
        }
        stage("push-image"){
            steps{
                withCredentials([usernamePassword(credentialsId:"dockerhub",passwordVariable:"pass",usernameVariable:"user")]){
                    sh "docker login -u ${env.user} -p ${env.pass}"
                    sh "docker tag appnotes:1.0 ${env.user}/appnotes:1.0"
                    sh "docker push ${env.user}/appnotes:1.0"
                    
                    echo "Push an image successfully"
                }
            }
        }
        stage("Deploy"){
            steps{
                 
                sh "docker-compose down && docker-compose up -d"
                echo "running container"
                 
            }
        }
    }
}
