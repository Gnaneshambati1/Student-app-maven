pipeline {
    agent any

    environment {
        APP_NAME = 'student-app'
        BUILD_ENV = 'development'
    }

    stages {

        stage('Verify Environment') {
            steps {
                echo "Application: ${APP_NAME}"
                echo "Environment: ${BUILD_ENV}"
                echo "Jenkins Build Number: ${BUILD_NUMBER}"
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
    }

    post {
        success {
            echo "Pipeline completed successfully"
        }

        failure {
            echo "Pipeline failed"
        }
    }
}
