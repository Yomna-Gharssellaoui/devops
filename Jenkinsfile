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
                echo "🔨 Building project with Maven..."
                sh 'mvn clean install'
            }
        }

        stage('Test') {
            steps {
                echo "🧪 Running unit tests..."
                sh 'mvn test'
            }
            post {
                always {
        // Correct path to Surefire test reports
                    junit 'target/surefire-reports/*.xml'
                    echo "📊 Test results published"
    }
}
            }
        }
    } // end of stages

    post {
        success {
            echo "✅ Pipeline succeeded!"
        }
        failure {
            echo "❌ Pipeline failed!"
        }
    }
} // end of pipeline
