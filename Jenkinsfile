@Library("Shared") _
pipeline {
    agent {label "ketaki-Agent"}

    stages {
        
        stage("Hello") {
            steps{
                script{
                    hello()
                }
            }
        }
        stage('Code clone') {
            steps {
                script{
                clone("https://github.com/KetakiJahagirdar/django-notes-app.git","main")
                }
            }
        }
        stage('Code build') {
            steps {
                echo 'build projekt'
                script{
                docker_build("notes-app","latest","ketaki123")
                }
            }
        }
        stage("Push to DockerHub"){
            steps{
                script{
                    docker_push("notes-app","latest","ketaki123")
                }

                }
            }
        stage("Deploy"){
            steps{
                echo "this is deploying the code"
                sh "docker compose down && docker compose up -d"
            }
        }

    }
}
