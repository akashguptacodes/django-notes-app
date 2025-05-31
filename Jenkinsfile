@Library("shared") _
pipeline{
    agent {label "agent1"}
    stages{
        stage("Hello"){
            steps{
                script{
                    hello()
                }
            }
        }
        stage("Code"){
            steps{
                script{
                    clone("https://github.com/LondheShubham153/django-notes-app.git","main")
                }
            }
        }
        stage("Build"){
            steps{
                script{
                    docker_build(imageName:"notes-app",imageTag: "latest",context:".")
                }
            }
        }
        stage("Push"){
            steps{
                script{
                    docker_push(imageName: "notes-app", imageTag: "latest", credentials: "dockerHubCred")
                }
            }
        }
        stage("Deploy"){
            steps{
                echo "Final step: deploying the app"
                sh "docker compose up -d"
            }
        }
    }
}
