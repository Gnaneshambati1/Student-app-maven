pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                echo 'Building application...'
                sh 'mvn clean package'
            }
        }

        stage('Verify Artifact') {
            steps {
                sh 'ls -lh target/*.jar'
            }
        }

        stage('Archive Artifact') {
            steps {
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            }
        }
    }

    post {

        always {
            echo 'Pipeline execution finished.'
        }

        success {
            echo 'SUCCESS: Build and artifact archiving completed.'
        }

        failure {
            echo 'FAILURE: Pipeline failed.'
        }
    }
}
