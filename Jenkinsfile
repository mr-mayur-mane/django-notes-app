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
        // stage("Code"){
        //     steps{
        //         echo "Cloning the code"
        //         git url: "https://github.com/mr-mayur-mane/django-notes-app.git", branch: "main"
        //     }
            
        // }
        // stage("build"){
        //     steps{
        //         echo "Building the docker image"
        //         sh "docker build -t my-note-app ."
        //     }
            
        // }
        // stage("Push to docker hub"){
        //     steps{
        //         echo "Pushing to docker hub"
        //         withCredentials([usernamePassword(credentialsId: "dockerHub",passwordVariable: "dockerHubPass", usernameVariable: "dockerHubUser")]){
        //         sh "docker tag my-note-app ${env.dockerHubUser}/my-note-app:latest"
        //         sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPass}"
        //         sh "docker push ${env.dockerHubUser}/my-note-app:latest"
        //         }
        //     }
        // }
        // stage("Depoyment"){
        //     steps{
        //         echo "Deploying the container"
        //         sh "docker compose down && docker compose up -d"
        //     }
        // }
    }   
        
}