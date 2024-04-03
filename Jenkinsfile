pipeline {
    agent any
    environment {
        SSH_USER = 'ubuntu'
        SERVER = '43.205.128.29'
        REMOTE_DIR = '~/jenkins-test'
    }
    stages {
        stage('Make directory') {
            steps {
                script {
                    try {
                        sh "ssh ${SSH_USER}@${SERVER} mkdir -p ${REMOTE_DIR}"
                    } catch (Exception e) {
                        echo "Failed to make directory"
                    }
                }
            }
        }
        stage('Make files') {
            steps {
                script {
                    sh "touch ${REMOTE_DIR}/file1"
                }
            }
        }
        stage('Build') {
            steps {
                echo 'Building...'
                sh "ssh ${SSH_USER}@${SERVER} ls -la ${REMOTE_DIR}"
            }
        }
        stage('Test') {
            steps {
                echo 'Testing...'
                sh "ssh ${SSH_USER}@${SERVER} pwd"
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying...'
                sh "ssh ${SSH_USER}@${SERVER} mv ${REMOTE_DIR}/file1 ${REMOTE_DIR}/file1_deployed"
            }
        }
    }
    post {
        always {
            echo 'This will always run'
        }
    }
}
