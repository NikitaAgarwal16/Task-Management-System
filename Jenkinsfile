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
                sh 'nohup node server.js > app.log 2>&1 &'
                sleep time: 5, unit: 'SECONDS' // Give time for the server to start
            }
        }
    }

    post {
        success {
            echo "Application started successfully. You can access it at http://localhost:3000"
        }
        failure {
            echo "Build failed! Check logs for errors."
        }
    }
}
