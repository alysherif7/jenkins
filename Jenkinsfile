pipeline {
    agent any

    environment {
        FIREBASE_TOKEN = credentials('firebase_token')
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Install Firebase Tools (local)') {
            steps {
                // install firebase-tools in this project (node_modules)
                bat 'npm install firebase-tools'
            }
        }

        stage('Deploy to Firebase') {
            steps {
                // use npx to run the local firebase binary
                bat 'npx firebase deploy --token %FIREBASE_TOKEN%'
            }
        }
    }
}