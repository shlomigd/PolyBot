pipeline {
    agent any

    stages {
        stage('Unittest') {
            steps {
                echo "testing"
                pip3 install pytest
                pip3 install unittest2
                sh 'python3 -m pytest --junitxml results.xml tests'
            }
        }
        stage('Functional test') {
            steps {
                echo "testing"
            }
        }
    }
    post {
    always {
        junit allowEmptyResults: true, testResults: 'results.xml'
    }
}
}