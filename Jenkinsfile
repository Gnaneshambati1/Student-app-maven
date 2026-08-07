pipeline {

    agent any

    stages {

        stage('Verify Workspace') {
            steps {
                sh '''
                pwd
                ls -la
                '''
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Verify Artifact') {
            steps {
                sh 'ls -la target'
            }
        }

    }

}
