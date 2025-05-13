@Library('Shared')_
pipeline{
    agent { label 'dev-server'}
    
    stages{
        stage("Code clone stage should be done"){
            steps{
                sh "whoami"
            clone("https://github.com/LondheShubham153/django-notes-app.git","main")
            }
        }
        stage("Code Build Stage"){
            steps{
            dockerbuild("notes-app","latest")
            }
        }
        stage("Push to DockerHub stage"){
            steps{
                dockerpush("dockerHubCreds","notes-app","latest")
            }
        }
        stage("Deploy stage"){
            steps{
                deploy()
            }
        }
        
    }
}
