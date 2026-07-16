pipeline {
    agent any

    environment {
        IMAGE_NAME = "janhavi070/jenkins-learning"
        IMAGE_TAG = "${env.BUILD_NUMBER}"
    }

    stages {

        stage('Run Tests') {
            steps {
                sh 'python3 test_app.py'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh '''
                docker build -t $IMAGE_NAME:latest .
                docker tag $IMAGE_NAME:latest $IMAGE_NAME:$IMAGE_TAG
                '''
            }
        }

        stage('Push Docker Image') {
            steps {
                withCredentials([
                    usernamePassword(
                        credentialsId: 'dockerhub',
                        usernameVariable: 'DOCKER_USER',
                        passwordVariable: 'DOCKER_PASS'
                    )
                ]) {

                    sh '''
                    echo "$DOCKER_PASS" | docker login -u "$DOCKER_USER" --password-stdin

                    docker push $IMAGE_NAME:latest
                    docker push $IMAGE_NAME:$IMAGE_TAG

                    docker logout
                    '''
                }
            }
        }

    }

    post {

        success {
            echo "Docker image pushed successfully!"
        }

        failure {
            echo "Pipeline failed."
        }

        always {
            echo "Pipeline finished."
        }

    }
}
