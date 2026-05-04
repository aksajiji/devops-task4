pipeline {
    agent any

    tools {
        maven 'Maven-3.9.6'    // Change this to match your Maven tool name in Jenkins
        jdk 'JDK-21'           // Change this to match your JDK tool name in Jenkins
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/aksajiji/devops-task4.git'
                // Replace YOUR_USERNAME with your actual GitHub username
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
                // For Windows agent, use: bat 'mvn clean package'
            }
        }

        stage('Deploy to Tomcat') {
            steps {
                deploy adapters: [
                    tomcat9(credentialsId: 'tomcat-credentials',
                            path: '',
                            url: 'http://localhost:8081/')
                ],
                contextPath: 'my-app-task4',
                war: 'target/*.war'
            }
        }
    }
}