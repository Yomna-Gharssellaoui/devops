pipeline {
    agent any

    environment {
        MVN_HOME        = '/usr/share/maven' 
        DOCKERHUB_USER  = 'yomnagharssellaoui03'
        IMAGE_NAME      = 'student-management'
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
                echo "🧪 Running tests..."
                sh "${MVN_HOME}/bin/mvn test"
            }
            post {
                always {
                    junit '**/target/surefire-reports/*.xml'
                    echo "📊 Test results published"
                }
            }
        }

        stage('Build Docker Image') {
            steps {
                echo "🐳 Building Docker image..."
                sh """
                    docker build -t ${DOCKERHUB_USER}/${IMAGE_NAME}:latest .
                """
            }
        }

        stage('Push Docker Image') {
            steps {
                echo "🚀 Pushing Docker image to DockerHub..."
                withCredentials([
                    usernamePassword(
                        credentialsId: 'docker-credentials', 
                        usernameVariable: 'DOCKER_USER',

