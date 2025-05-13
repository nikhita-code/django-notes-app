@Library("Shared") _
pipeline {
    agent { label "vinod" }

    environment {
        IMAGE_NAME = "notes-app"
        TAG = "latest"
    }

    stages {
        stage("Hello") {
            steps {
                script{ 
                    hello()
                }
            }
        }
        stage("Code") {
            steps {
                script{
                clone("https://github.com/nikhita-code/django-notes-app.git","main")
                }
            }
        }

        stage("Build") {
            steps {
               script{
               docker_build("notes-app", "latest", "dockerhub9820")
               }
            }
        }

        stage("Test") {
            steps {
                echo "Testing stage placeholder."
            }
        }

        stage("Push to DockerHub") {
            steps {
               script{
                   docker_push("notes-app", "latest", "dockerhub9820") 
               }
            }
        }

        stage("Deploy") {
            steps {
                echo "Deploying using Docker Compose..."
                sh "docker compose down && docker compose up -d"
            }
        }
    }
}
