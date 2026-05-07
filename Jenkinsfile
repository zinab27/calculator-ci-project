pipeline {
    agent any

    stages {

        stage('Clone Repository') {
            steps {
                echo 'Cloning repository from GitHub...'
                git branch: 'main', url: 'https://github.com/zinab27/Calculator-CI.git'
            }
        }

        stage('Build') {
            steps {
                echo 'Building the project with Maven...'
                bat 'mvn clean compile'
            }
        }

        stage('Run Unit Tests') {
            steps {
                echo 'Running JUnit tests...'
                bat 'mvn test'
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
            echo 'Pipeline completed successfully! All tests passed.'
        }
        failure {
            echo 'Pipeline failed. Check the test results above.'
        }
    }
}