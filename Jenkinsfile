pipeline {
    agent any
    environment {
        MERGIFY_TOKEN = credentials('MERGIFY_TOKEN')
    }
    stages {
        stage('Checking environment') {
            steps {
                sh 'set'
                sh 'echo $MERGIFY_TRACEPARENT'
            }
        }
        stage('Running pytest tests') {
            steps {
                sh 'echo $MERGIFY_TRACEPARENT'
                sh '''
                export MERGIFY_TEST_JOB_NAME=jenkins-build-py313-pipeline 
                tox run -r -e py313 -- testing/test_config.py
                '''
            }
        }
    }
}

