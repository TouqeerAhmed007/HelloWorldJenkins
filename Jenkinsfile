pipeline {
    agent any
    environment {
        VERSION = '1.0.0'
        APP_NAME = 'MyAwesomeApp'
    }
    stages {
        stage('Build') {
            steps {
                echo 'Building..'
                echo "Building version ${VERSION} of ${APP_NAME}"
            }
        }
        stage('Test') {
            when {
                expression { 
                    return true
                }
            }
            steps {
                echo 'Testing..'
                echo "Testing ${APP_NAME}"
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
                echo "Deploying ${APP_NAME} version ${VERSION}"
            }
        }
    }
    post {
        always {
            echo 'This will always run after all stages'
        }
        success {
            echo 'This will run only if the build is successful'
        }
        failure {
            echo 'This will run only if the build fails'
        }
    }
}
