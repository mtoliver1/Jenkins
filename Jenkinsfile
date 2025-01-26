pipeline {
    agent any

    tools {
        // Install the Maven version configured as "M3" and add it to the path.
        maven "3.9.9"
    }

    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/mtoliver1/Jenkins.git'
            }
        }
        stage('Build') {
            steps {
                dat 'mvn -Dmaven.test.failure.ignore=true clean package'
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
