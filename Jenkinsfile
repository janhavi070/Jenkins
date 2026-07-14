pipeline {
    agent any

    stages {

        stage('Run Application') {
            steps {
                sh 'python3 app.py'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'python3 test_app.py'
            }
        }
    }
}
