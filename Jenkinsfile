pipeline {
    agent any
    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/sunitsai/ToDo-Pipeline.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t todo-app .'
            }
        }
        stage('Run Tests') {
            steps {
                sh 'pytest || echo "Tests failed, but continuing..."'
            }
        }
        stage('Push to Docker Hub') {
            steps {
                sh 'docker login -u your-username -p your-password'
                sh 'docker tag todo-app your-username/todo-app'
                sh 'docker push your-username/todo-app'
            }
        }
        stage('Deploy on Local Machine') {
            steps {
                sh 'docker run -d -p 5000:5000 your-username/todo-app'
            }
        }
    }
}
