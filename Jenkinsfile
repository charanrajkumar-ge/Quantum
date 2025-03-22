pipeline {
    agent any

    parameters {
        string(name: 'VERSION', defaultValue: '1.0.0', description: 'Application Version')
        booleanParam(name: 'DEPLOY', defaultValue: false, description: 'Deploy to production?')
        choice(name: 'ENVIRONMENT', choices: ['DEV', 'QA', 'PROD'], description: 'Choose deployment environment')
    }

    stages {
        stage('Build') {
            steps {
                echo "Building version: ${params.VERSION}"
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
            }
        }

        stage('Deploy') {
            when {
                expression { params.DEPLOY.toBoolean() }
            }
            steps {
                echo "Deploying to ${params.ENVIRONMENT} environment..."
            }
        }
    }

    post {
        always {
            echo 'Pipeline execution completed!'
        }
    }
}
