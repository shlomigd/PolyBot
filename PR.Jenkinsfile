pipeline {
    agent any

    stages {
        stage('Unittest') {
            steps {
                sh '''
                pip3 install -r requirements.txt
                python3 -m pytest --junitxml results.xml tests
                python -m pylint -f parseable --reports=no *.py > pylint.log
                '''
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
        sh 'cat pylint.log'
        recordIssues (
          enabledForFailure: true,
          aggregatingResults: true,
          tools: [pyLint(name: 'Pylint', pattern: '**/pylint.log')]
        )
    }
}
}