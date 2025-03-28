@Library("Shared") _
pipeline{
    
    agent { label "gaurav" }
    
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
                 clone("https://github.com/gauravv-1/django-notes-app.git", "main")
                }
                
            }
            
        }
        stage("Build"){
            steps{
                script{
                    docker_build("notes-app","latest","pisal23")
                }
                
            }
        }
        stage("Push to DockerHub"){
            steps{
                script{
                    docker_push("notes-app","latest","pisal23")
                }
            }
        }
        stage("Deploy"){
            steps{
                echo "This is Deploying the code"
                sh "docker compose up -d"
                echo "Sucessfully Deployed the code"
            }
        }
    }
}
