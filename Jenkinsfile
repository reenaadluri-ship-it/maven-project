
pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out Maven Web Project'
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Building the web application'
                sh 'mvn clean package -DskipTests'
            }
        }

        stage('Test') {
            steps {
                echo 'Running Maven tests'
                sh 'mvn test'
            }
        }

        stage('Package') {
            steps {
                echo 'Packaging WAR file'
                archiveArtifacts artifacts: 'target/*.war',
                                 fingerprint: true
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed. Check the console output.'
        }
    }
}
