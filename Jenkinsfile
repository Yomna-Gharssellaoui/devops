pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo "🔁 Checking out repository..."
                git branch: 'main', url: 'https://github.com/yumiiiiiiiiiiiiiiiiiiiiiiii/devops.git'
            }
        }

        stage('Build') {
            steps {
                echo "🔨Building project with Maven..."
                sh 'mvn clean install'
            }
        }
    }

    post {
        success {
            echo "✅ Pipeline succeeded!"
        }
        failure {
            echo "❌Pipeline failed!"
        }
    }
}
