pipeline {
    agent any

    stages {

        stage('Test Credential') {
            steps {
                withCredentials([
                    string(
                        credentialsId: 'cicd-lab-secret',
                        variable: 'MY_SECRET'
                    )
                ]) {
                    sh '''
                        echo "Credential is available to the pipeline"
                        echo "Secret length: ${#MY_SECRET}"
                    '''
                }
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
    }

    post {
        always {
            echo 'Pipeline execution finished.'
        }

        success {
            echo 'Pipeline completed successfully.'
        }

        failure {
            echo 'Pipeline failed.'
        }
    }
}
