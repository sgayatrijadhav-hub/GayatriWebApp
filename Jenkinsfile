pipeline {
    agent any

    tools {
        maven 'Maven'
    }

    stages {

        stage('Checkout SCM') {
            steps {
                git branch: 'main',
                url: 'https://github.com/sgayatrijadhav-hub/GayatriWebApp.git'
            }
        }

        stage('Tool Install') {
            steps {
                sh 'java -version'
                sh 'mvn -v'
                sh 'ansible --version'
            }
        }

        stage('Compile') {
            steps {
                sh 'mvn compile'
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

        stage('Deploy WAR') {
            steps {
                sh 'ansible-playbook deploy.yml'
            }
        }

        stage('Verify Files') {
            steps {
                sh 'ls /opt/tomcat9/webapps'
            }
        }
    }
}
