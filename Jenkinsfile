pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                echo 'Installing Python dependencies...'
                sh '''
                    python3 -m venv venv
                    . venv/bin/activate
                    python -m pip install --upgrade pip
                    pip install -r requirements.txt
                '''
            }
        }

        stage('Test') {
            steps {
                echo 'Running Unit Tests...'
                sh '''
                    . venv/bin/activate
                    pytest test_app.py
                '''
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying Flask Application...'
                sh '''
                    chmod +x start_flask.sh
                    ./start_flask.sh
                '''
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
