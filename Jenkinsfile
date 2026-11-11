post {
    success {
        emailext(
            subject: "SUCCESS: ${JOB_NAME} #${BUILD_NUMBER}",
            body: "Build completed successfully.\nCheck Jenkins: ${BUILD_URL}",
            to: "YOUR_EMAIL@gmail.com"
        )
    }

    failure {
        emailext(
            subject: "FAILED: ${JOB_NAME} #${BUILD_NUMBER}",
            body: "Build failed. Please check the console output: ${BUILD_URL}",
            to: "YOUR_EMAIL@gmail.com"
        )
    }
}
