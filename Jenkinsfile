pipeline {
    agent any
    tools {
        maven 'Maven3'
    }
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build Image') {
            steps {
                sh 'docker build -t team-skeleton:latest ./starter'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn -B test -f ./starter/pom.xml'
            }
            post {
                always {
                    junit 'starter/target/surefire-reports/*.xml'
                }
            }
        }
    }
}