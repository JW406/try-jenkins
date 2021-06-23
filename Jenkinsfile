pipeline {
    agent {
        label 'master'
    }
    stages {
        stage('Build') {
            steps {
                echo 'Building'
                sh 'which java'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing'
            }
        }
        stage('Deploy - Staging') {
            steps {
                echo 'sh ./deploy staging'
                echo 'sh ./run-smoke-tests'
            }
        }
        stage('Sanity check') {
            steps {
                echo "input Does the staging environment look ok?"
            }
        }
        stage('Deploy - Production') {
            steps {
                echo './deploy production'
            }
        }
    }
    post {
        always {
            echo 'One way or another, I have finished'
            echo 'deleting dir'
        }
        success {
            echo 'I succeeeded!'
        }
        unstable {
            echo 'I am unstable :/'
        }
        failure {
            echo 'I failed :('
        }
        changed {
            echo 'Things were different before...'
        }
    }
}
