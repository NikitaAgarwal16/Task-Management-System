pipeline {
    agent any

    environment {
        NODE_HOME = tool name: 'NodeJS 16', type: 'jenkins.plugins.nodejs.tools.NodeJSInstallation'
        PATH = "${NODE_HOME}/bin:${env.PATH}"
    }

    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/NikitaAgarwal16/Task-Management-System.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Run Unit Tests') {
            steps {
                sh 'npm test || echo "Tests failed, but continuing..."'
            }
        }

        stage('Start Application') {
            steps {
                sh 'node server.js &'
            }
        }
    }
}
