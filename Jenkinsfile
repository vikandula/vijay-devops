pipeline {
    agent { label 'ubuntu' } // Ensure this runs on an Ubuntu node/agent
    
    echo "✅ Message from Jenkinsfile."
    
    stages {
        stage('Clone Repository') {
            steps {
                // Replace with your public repo URL
                git branch: 'main', url: 'https://github.com/octocat/Hello-World.git'
            }
        }

        stage('Zip Repository Files') {
            steps {
                script {
                    // Create a zip of the entire workspace
                    zip zipFile: 'repo.zip', archive: true, dir: '.'
                }
            }
        }
    }

    post {
        success {
            echo "✅ Repository zipped and archived successfully."
        }
        failure {
            echo "❌ Pipeline failed."
        }
    }
}
