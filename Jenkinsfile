pipeline {
    agent any
environment {
        MAVEN_HOME = tool 'MAVEN'
      }
    stages {
        stage('Checkout Code') {
            steps {
                echo "� Cloning Private GitHub Repository..."
                 git credentialsId: 'my-private-repo-creds', branch: 'main', url: 'https://github.com/Shivani-1998-Devops/superlab.git'
            }
        }

        stage('Maven Build') { 
            steps { 
                echo 'Building project' 
                sh "${MAVEN_HOME}/bin/mvn clean verify -Dtest=!FormUITest" 
            } 
        }

        // ➕ Add more stages as needed
    }

    post {
        success {
            echo "✅ Pipeline completed successfully!"
        }
        failure {
            echo "❌ Pipeline failed. Please check the logs."
        }
    }
}