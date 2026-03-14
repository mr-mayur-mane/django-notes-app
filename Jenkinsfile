@Library("Shared") _
pipeline{
    agent any
    stages{
        stage("Clean workspace"){
            steps{
                cleanWs()
            }
        }
        stage("hello"){
            steps{

                hello()
                
            }
        }
        stage("Code"){
            steps{
                clone("https://github.com/mr-mayur-mane/django-notes-app.git","main")
            }
            
        }
        stage("build"){
            steps{
                
                docker_build("notes-app","latest","mayur0607")
            }
            
        }
        stage("Push to docker hub"){
            steps{
                docker_push("notes-app","latest","mayur0607")
                }
            }
        
        stage("Depoyment"){
            steps{
                echo "Deploying the container"
                sh "docker compose down && docker compose up -d"
            }
        }
    }   
        
}