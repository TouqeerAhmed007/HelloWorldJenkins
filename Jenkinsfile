pipeline {
    agent any
    parameters {
        string(name: 'VERSION', defaultValue: '1.0.0', description: 'Version to deploy')
        choice(name: 'ENVIRONMENT', choices: ['dev', 'staging', 'production'], description: 'Target environment')
        booleanParam(name: 'executeTests', defaultValue: true, description: 'Execute test stage?')
    }
    environment {
        APP_NAME = 'MyAwesomeApp'
    }
    stages {
        stage('Build') {
            steps {
                echo 'Building..'
                echo "Building version ${params.VERSION} of ${APP_NAME}"
            }
        }
        stage('Test') {
            when {
                expression { 
                    return params.executeTests == true
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
                echo "Deploying ${APP_NAME} version ${params.VERSION} to ${params.ENVIRONMENT}"
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
