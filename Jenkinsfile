pipeline {
    agent any
    stages {
        stage('Make directory') {
            steps {
                script {
                    try {
                        sh "mkdir ~/jenkins-test"
                    } catch (Exception e) {
                        echo "Failed to make directory"
                    }
                }
            }
        }
        stage('Make files') {
            steps {
                sh 'touch ~/jenkins-test/file1'
            }
        }
        stage('Build') {
            steps {
                echo 'Building...'
                sh 'ls -la ~/jenkins-test'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing...'
                sh 'pwd'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying...'
                sh 'mv ~/jenkins-test/file1 ~/jenkins-test/file1_deployed'
            }
        }
    }
    post {
        always {
            echo 'This will always run'
        }
    }
}
