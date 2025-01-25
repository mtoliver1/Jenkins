pipeline {
    agent any

    tools {
        // Use the Maven version configured in Jenkins
        maven 'Maven_3.9.9' // Replace with the Maven version you configured
    }

    stages {
        stage('Clone Repository') {
            steps {
                // Clone the GitHub repository
                git 'https://github.com/mtoliver1/Jenkins.git' // Replace with your repository URL
            }
        }

        stage('Build') {
            steps {
                // Run Maven build
                sh 'mvn clean install'
            }
        }

        stage('Test') {
            steps {
                // Run Maven tests
                sh 'mvn test'
            }
        }

        stage('Package') {
            steps {
                // Package the application (e.g., JAR or WAR)
                sh 'mvn package'
            }
        }

        stage('Archive Artifacts') {
            steps {
                // Archive build artifacts
                archiveArtifacts artifacts: '**/target/*.jar', fingerprint: true
            }
        }
    }

    post {
        always {
            echo 'Pipeline execution completed!'
        }

        success {
            echo 'Build and test completed successfully!'
        }

        failure {
            echo 'Pipeline failed. Check logs for errors.'
        }
    }
}
