pipeline {
    agent any
    
    environment {
        VERSION = '1.0.0'
    }
    
    parameters {
        booleanParam(name: 'executeTests', defaultValue: true)
    }
    
    stages {
        stage('Build') {
            steps {
                echo 'Building..'
                echo "Version: ${VERSION}"
                sh 'echo "Build stage completed on Ubuntu"'
                sh 'uname -a'
            }
        }
        
        stage('Maven Build') {
            steps {
                echo 'Testing Maven installation..'
                sh 'mvn --version'  // ← Test Maven is available
                sh 'mvn clean compile -DskipTests'  // ← Basic Maven command
            }
        }
        
        stage('Test') {
            when {
                expression { params.executeTests == true }
            }
            steps {
                echo 'Testing..'
                sh 'echo "Test stage running on Ubuntu"'
            }
        }
        
        stage('Deploy') {
            steps {
                echo 'Deploying....'
                sh 'echo "Deployment stage on Ubuntu"'
            }
        }
    }
    
    post {
        always {
            echo 'Pipeline Completed Successfully!'
            echo 'Pipeline Completed'
        }
    }
}
