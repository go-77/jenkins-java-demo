pipeline {
    agent any

    tools {
        maven 'Maven3'   // configured in Jenkins
        jdk 'JDK17'      // configured in Jenkins
    }

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/<your-username>/jenkins-java-demo.git'
            }
        }

        stage('Build') {
            steps {
                echo 'Building Java project with Maven...'
                sh 'mvn clean install'
            }
        }

        stage('Test') {
            steps {
                echo 'Running unit tests...'
                sh 'mvn test'
            }
            post {
                always {
                    junit '**/target/surefire-reports/*.xml'
                }
            }
        }
    }

    post {
        success {
            echo 'Java Pipeline succeeded!'
        }
        failure {
            echo 'Java Pipeline failed!'
        }
    }
}

