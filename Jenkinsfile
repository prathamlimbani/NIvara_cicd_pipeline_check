pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo "Code checked out"
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t devops-demo:v1 .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh 'docker ps -q | xargs -r docker stop'
            }
        }

        stage('Deploy Container') {
            steps {
                sh 'docker run -d -p 80:3000 devops-demo:v1'
            }
        }

        stage('Verify Deployment') {
            steps {
                echo "Deployment done"
            }
        }
    }

    post {
        always {
            echo "Pipeline finished"
        }
    }
}
