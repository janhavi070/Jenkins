pipeline {
    agent any

    stages {

        stage('Show Workspace') {
            steps {
                echo 'Current Workspace'
                sh 'pwd'
            }
        }

        stage('List Files') {
            steps {
                sh 'ls -la'
            }
        }

        stage('Run Python App') {
            steps {
                sh 'python3 app.py'
            }
        }

    }
}
