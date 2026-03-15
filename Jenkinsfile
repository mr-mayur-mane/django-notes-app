@Library("Shared") _
pipeline{
    agent any
    environment{
        SONAR_HOME = tool "Sonar"
    }
    stages{
        stage("Clean workspace"){
            steps{
                cleanWs()
            }
        }
        stage("Code"){
            steps{
                clone("https://github.com/mr-mayur-mane/django-notes-app.git","main")
            }
            
        }
        stage("Trivy filesystem scan"){
            steps{
                trivy_scan()
            }
        }
        stage("OWASP Dependency check"){
            owasp_dependency()
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
        
        stage("Deployment"){
            steps{
                echo "Deploying the container"
                sh "docker compose down && docker compose up -d"
            }
        }
    }   
        
}