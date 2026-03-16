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
        stage("hello shared lib"){
            steps{
                hello()
            }
        }
        
        stage("Trivy filesystem scan"){
            steps{
                trivy_Scan()
            }
        }
        stage("OWASP Dependency check"){
            steps{
                owasp_dependency()
            }
        }
        // stage("SonarQube: Code Analysis"){
        //     steps{
        //         sonarqube_code_analysis("Sonar", "notes-app", "notes-app")
        //     }
        // 
        // }   
        stage("SonarQube: Code Quality Gates"){
            steps{
                sonarqube_code_quality()
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
        
        stage("Deployment"){
            steps{
                echo "Deploying the container"
                sh "docker compose down && docker compose up -d"
            }
        }
    }   
        
}