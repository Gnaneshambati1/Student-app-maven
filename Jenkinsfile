pipeline {
    agent any

    parameters {
        choice(
            name: 'ENVIRONMENT',
            choices: ['development', 'testing', 'production'],
            description: 'Select the deployment environment'
        )

        string(
            name: 'APP_VERSION',
            defaultValue: '1.0',
            description: 'Enter application version'
        )

        booleanParam(
            name: 'RUN_TESTS',
            defaultValue: true,
            description: 'Run unit tests?'
        )
    }

    stages {

        stage('Show Parameters') {
            steps {
                echo "Environment: ${params.ENVIRONMENT}"
                echo "Application Version: ${params.APP_VERSION}"
                echo "Run Tests: ${params.RUN_TESTS}"
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
