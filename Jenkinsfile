pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/benlau0402/jenkins_ngrok.git'
            }
        }
        stage('Build') {
            steps { sh './gradlew build'}
        }
        stage('Test') {
            steps { sh './gradlew test'} 
        }
        stage('Deploy') {
            steps {
                sh '''
                echo "Running JAR on Unix..."
                java -jar build/libs/hello-world-java-V1.jar
                '''
            }
        }
    }
post {
        always {
            echo 'Cleaning up workspace'
            deleteDir() // Clean up the workspace after the build
        }
        success {
            echo 'Build succeeded!!!'
            // You could add notification steps here
        }
        failure {
            echo 'Build failed!'
            // You could add notification steps here
        }
    }
}
