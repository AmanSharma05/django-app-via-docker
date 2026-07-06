@Library("shared") _
pipeline{
    
    agent { label "Aman"}
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
                    clone("https://github.com/AmanSharma05/django-app-via-docker.git", "main")
                }
            }
        }
        stage("Build"){
            steps{
                script{
                    docker_build("notes-app", "latest", "amansharma0511")
                }
            }
        }
        stage("Push to DockerHub"){
            steps{
                script{
                    docker_push("notes-app", "latest", "amansharma0511")
                }
            }
        }
        stage("Deploy"){
            steps{
                sh '''
                pwd
                docker compose down
                docker compose pull
                docker compose up -d
                docker compose ps
                docker compose ps -a
                '''
            }
        }
    }
}
