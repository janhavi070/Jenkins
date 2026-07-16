pipeline {
    agent any

    stages {

        stage('Run Tests') {
            steps {
                sh 'python3 test_app.py'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t jenkins-learning:v1 .'
            }
        }

    }

    post {
        success {
            echo 'Docker image built successfully!'
        }

        failure {
            echo 'Pipeline failed.'
        }

        always {
            echo 'Pipeline finished.'
        }
    }
}
