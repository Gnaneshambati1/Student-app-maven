pipeline {
    agent any

    parameters {
        choice(
            name: 'ENVIRONMENT',
            choices: ['development', 'testing', 'production'],
            description: 'Select the environment'
        )
    }

    stages {

        stage('Show Environment') {
            steps {
                echo "Selected Environment: ${params.ENVIRONMENT}"
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Development Test') {
            when {
                expression {
                    params.ENVIRONMENT == 'development'
                }
            }

            steps {
                echo 'Running development testing...'
            }
        }

        stage('Testing Validation') {
            when {
                expression {
                    params.ENVIRONMENT == 'testing'
                }
            }

            steps {
                echo 'Running testing environment validation...'
            }
        }

        stage('Production Validation') {
            when {
                expression {
                    params.ENVIRONMENT == 'production'
                }
            }

            steps {
                echo 'Running production validation...'
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully'
        }

        failure {
            echo 'Pipeline failed'
        }
    }
}
