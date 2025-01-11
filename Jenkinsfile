@Library("Shared") _
pipeline {
    agent {label "slave"}

    stages {
        stage('Code') {
            steps {
                script {
                    clone("https://github.com/prabhatkhande/django-todo-cicd.git", "develop")
                }
            }
        }
        stage('Build') {
            steps {
                script {
                    docker_build("notes-app", "latest", "prabhat332")  
                }
            }
        }
        stage('Pushing to Docker Hub') {
            steps {
               script {
                docker_push("notes-app", "latest", "prabhat332")
                }
            }
        }
        stage('Deploy') {
            steps {
                echo 'This is deploying the image'
                sh "docker compose down && docker compose up -d"
            }
        }
    }
}
