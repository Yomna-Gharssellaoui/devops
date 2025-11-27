pipeline {
    agent any

    environment {
        MVN_HOME = '/usr/share/maven' // adapte selon ton installation Maven
    }

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
                sh "${MVN_HOME}/bin/mvn clean install"
            }
        }

        stage('Test') {
            steps {
                echo "🧪 Running unit tests..."
                sh "${MVN_HOME}/bin/mvn test"
            }
            post {
                always {
                    // attention au chemin exact des rapports générés par Surefire
                    junit '**/target/surefire-reports/*.xml'
                    echo "📊 Test results published"
                }
            }
        }
    }

    post {
        success {
            echo "✅ Pipeline succeeded!"
        }
        failure {
            echo "❌ Pipeline failed!"
        }
    }
}
