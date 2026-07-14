pipeline {
    agent any

    environment {
        APP_NAME = "jenkins-learning"
    }

    stages {

        stage('Jenkins Variables') {
            steps {
                echo "Application: ${env.APP_NAME}"
                echo "Build Number: ${env.BUILD_NUMBER}"
                echo "Job Name: ${env.JOB_NAME}"
            }
        }

        stage('Shell Variables') {
            steps {
                sh 'echo "App: $APP_NAME"'
                sh 'echo "Workspace: $WORKSPACE"'
                sh 'echo "Build: $BUILD_NUMBER"'
            }
        }
    }
}
