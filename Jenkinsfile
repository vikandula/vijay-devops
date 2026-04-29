pipeline {
   agent any // Use any available agent/node to execute the pipeline
   stages {
       stage('Checkout Code') {
           steps {
               // Clone the repository from Git
               git branch: 'main', url: 'https://github.com/example/repo.git'
           }
       }
       stage('Build') {
           steps {
               // Run a build command (e.g., Maven or Gradle)
               sh 'mvn clean package'
           }
       }
       stage('Test') {
           steps {
               // Run unit tests
               sh 'mvn test'
           }
       }
       stage('Deploy') {
           steps {
               // Deploy the application (e.g., copy files to a server)
               sh 'scp target/app.jar user@server:/path/to/deploy'
           }
       }
   }
   post {
       always {
           // Archive build artifacts regardless of success or failure
           archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
       }
       success {
           // Notify on success
           echo 'Pipeline completed successfully!'
       }
       failure {
           // Notify on failure
           echo 'Pipeline failed. Please check the logs.'
       }
   }
}
