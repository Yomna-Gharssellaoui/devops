pipeline {
    agent any

    stages {
        stage('Webhook Test') {
            steps {
                echo "🚀Webhook triggered successfully!"
                sh 'date'
                sh 'echo "Commit received from GitHub"'
            }
        }
    }

    post {
        success {
            echo "✅ Build triggered OK"
        }
        failure {
            echo "❌Something went wrong"
        }
    }
}
