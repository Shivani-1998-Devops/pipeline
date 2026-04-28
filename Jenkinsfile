pipeline {
    agent any

    environment {
        MAVEN_HOME = tool 'MAVEN'
    }
    stages {
        stage('Checkout Code') {
            steps {
                echo 'Cloning repository...'
                git credentialsId: 'my-private-repo-creds',
                    branch: 'main',
                    url: 'https://github.com/Shivani-1998-Devops/superlab.git'
            }
        }
        stage('Maven Build') {
            steps {
                echo 'Building project'
                sh 'mvn clean verify -Dtest=!FormUITest'
            }
        }
    }

    post {
        success {
            echo 'Build successfull'
        }
        failure {
            echo 'Build failed'
        }
    }
}