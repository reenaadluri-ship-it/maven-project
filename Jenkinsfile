
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
                echo 'Building Web Application'
                bat 'mvn clean package -DskipTests'
            }
        }

        stage('Test') {
            steps {
                echo 'Running Tests'
                bat 'mvn test'
            }
        }

        stage('Package') {
            steps {
                echo 'Packaging WAR File'
                archiveArtifacts artifacts: 'target/*.war',
                                 fingerprint: true
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying Web Application'
                bat '''
                if not exist C:\\JenkinsDeploy mkdir C:\\JenkinsDeploy
                copy /Y target\\webproject.war C:\\JenkinsDeploy\\webproject.war
                '''
            }
        }
    }

    post {
        success {
            emailext(
                subject: "SUCCESS: ${JOB_NAME} #${BUILD_NUMBER}",
                body: "Build, Test and Deployment completed successfully. Check: ${BUILD_URL}",
                to: "reenaadluri@gmail.com"
            )
        }

        failure {
            emailext(
                subject: "FAILED: ${JOB_NAME} #${BUILD_NUMBER}",
                body: "Pipeline failed. Check Console Output: ${BUILD_URL}",
                to: "YOUR_EMAIL@gmail.com"
            )
        }
    }
}
