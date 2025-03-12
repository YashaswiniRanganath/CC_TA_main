pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                script {
                    try {
                        sh 'g++ -o my_program main.cpp'
                        echo 'Build successful'
                    } catch (Exception e) {
                        error 'Build failed'
                    }
                }
            }
        }
        
        stage('Test') {
            steps {
                script {
                    try {
                        sh './my_program'
                        echo 'Tests passed'
                    } catch (Exception e) {
                        error 'Tests failed'
                    }
                }
            }
        }
        
        stage('Deploy') {
            steps {
                script {
                    try {
                        sh 'scp my_program user@server:/deploy/path'
                        echo 'Deployment successful'
                    } catch (Exception e) {
                        error 'Deployment failed'
                    }
                }
            }
        }
    }
    
    post {
        failure {
            echo 'Pipeline failed'
        }
    }
}
