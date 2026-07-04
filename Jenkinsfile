pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                echo 'Installing Python dependencies...'
                sh 'python3 -m pip install --upgrade pip'
                sh 'pip3 install -r requirements.txt'
            }
        }

        stage('Test') {
            steps {
                echo 'Running Unit Tests...'
                sh 'pytest test_app.py'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying Flask Application...'
                sh 'chmod +x start_flask.sh'
                sh './start_flask.sh'
            }
        }
    }

    post {
        success {
            echo 'Pipeline executed successfully!'
        }

        failure {
            echo 'Pipeline failed!'
        }

        always {
            echo 'Pipeline execution completed.'
        }
    }
}
