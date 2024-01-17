pipeline {
    agent any
    
    environment {
        MAVEN_HOME = tool 'Maven'
    }

    stages {
        stage('Checkout') {
            steps {
                script {
                    checkout(
                        [
                            $class: 'GitSCM',
                            branches: [[name: '*/main']],
                            userRemoteConfigs: [[
                                credentialsId: 'token-jenkins',
                                url: 'https://github.com/Nimraaa18/GitTestRepo.git'
                            ]]
                        ]
                    )
                }
            }
        }

        stage('Build') {
            steps {
                script {
                    // Build the Java project using Maven
                    sh "${MAVEN_HOME}/bin/mvn clean install"
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    // Run tests using Maven
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


