pipeline {
    agent any
    
    environment {
        MAVEN_HOME = tool 'Maven' // Use the Maven tool configured in Jenkins
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout the source code from the repository
                checkout scm
            }
        }

        stage('Build') {
            steps {
                // Build the Java project using Maven
                script {
                    sh "${MAVEN_HOME}/bin/mvn clean install"
                }
            }
        }

        stage('Test') {
            steps {
                // Run tests using Maven
                script {
                    sh "${MAVEN_HOME}/bin/mvn test"
                }
            }
        }
    }

    post {
        success {
            echo 'Build and test succeeded. Deploying or performing additional actions...'
            // Add deployment steps or other post-build actions for success
        }
        failure {
            echo 'Build or test failed. Taking corrective actions...'
            // Add actions to be taken in case of failure
        }
        always {
            echo 'This will always run, regardless of the build result.'
            // Add any cleanup or finalization steps
        }
    }
}

