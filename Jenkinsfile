pipeline {
    agent any
    tools {
        maven 'maven' // Use Maven from Jenkins global tool configuration
        jdk 'jdk11' // Use JDK11 from Jenkins global tool configuration
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'master', url: 'https://your-git-repo-url'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean compile'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
        stage('Package') {
            steps {
                sh 'mvn package'
            }
        }
    }
    post {
        always {
            junit '**/target/surefire-reports/*.xml' // Collect test reports
            archiveArtifacts artifacts: '**/target/*.jar', fingerprint: true
        }
    }
}
