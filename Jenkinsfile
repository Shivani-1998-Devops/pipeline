pipeline {
    agent any

    environment {
        MAVEN_HOME = tool 'MAVEN'
        JAVA_HOME = '/usr/lib/jvm/java-21-openjdk-amd64'
        PATH = "${JAVA_HOME}/bin:${MAVEN_HOME}/bin:${env.PATH}"
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

        stage('Check Java') {
            steps {
                sh 'java -version'
                sh 'javac -version'
                sh 'echo $JAVA_HOME'
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
            echo 'Build successful'
        }
        failure {
            echo 'Build failed'
        }
    }
}