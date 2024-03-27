pipeline {
  agent any

  stages {
    stage('Build') {
      steps {
        script {
          // Clone the Git repository
          git 'https://github.com/nileshsurya1994/nodejs-app.git'

          // Read the Dockerfile
          def dockerfile = readFile('Dockerfile')

          // Write the Dockerfile to the workspace
          writeFile file: 'Dockerfile', text: dockerfile

          // Build Docker image
          sh 'docker build -t my-node-app .'
        }
      }
    }
    stage('Test') {
      steps {
        // Add test steps if applicable
      }
    }
    stage('Deploy') {
      steps {
        // Run Docker container
        sh 'docker run -d -p 3000:3000 --name my-node-container my-node-app'
      }
    }
  }
  post {
    always {
      // Stop Docker container
      sh 'docker stop my-node-container'

      // Remove Docker container
      sh 'docker rm my-node-container'
    }
  }
}
