@Library("shared") _
pipeline {
    agent { label 'slave1'}

    stages {
        stage('cleaning docker'){
            steps {
                script{cleanse_docker()}
            }
        }
        stage('Cloning Repository') {
            steps {
                echo 'Cloning'
                script{
                    clone.cloneRepo("https://github.com/Its-Akhil/django-notes-app-trainWithShubham.git","main")
                }
            }
        }
        stage('Build') {
            steps {
                script{ build_docker() }
            }
        }
        stage('Push To DockerHub'){
            steps{
                script{ 
                    dockerhub_push("DockerHub","jenkins-notes-app","latest ") 
                }
            }
        }
        stage('Test') {
            steps {
                echo 'Testing Shared Library Connection'
                
            }
        }
        stage('Deploy') {
            steps {
                script{
                    deploy()
                }
            }
        }
    }
}
