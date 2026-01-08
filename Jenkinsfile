pipeline {
    agent any

    tools {
        maven 'Maven'
        jdk 'JDK17'
    }

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Archive') {
            steps {
                archiveArtifacts artifacts: 'target/*.jar'
            }
        }
    }

    post {
        success {
            slackSend(
                channel: '#jenkins-notifications',
                color: 'good',
                message: "✅ Jenkins Pipeline SUCCESS: PipeLine-OussamaTalibi"
            )
        }
        failure {
            slackSend(
                channel: '#jenkins-notifications',
                color: 'danger',
                message: "❌ Jenkins Pipeline FAILED: PipeLine-OussamaTalibi"
            )
        }
    }
}
