pipeline {
  agent any

  stages {
    stage('Build') {
      steps {
        git 'https://github.com/nileshsurya1994/nodejs-app.git' // Clone the Git repository
        script {
          def dockerfile = readFile('Dockerfile') // Read the Dockerfile
          writeFile file: 'Dockerfile', text: dockerfile // Write the Dockerfile to the workspace
        }
        sh 'docker build -t my-node-app .' // Build Docker image
      }
    }
    stage('Test') {
      steps {
        // Add test steps if applicable
      }
    }
    stage('Deploy') {
      steps {
        sh 'docker run -d -p 3000:3000 --name my-node-container my-node-app' // Run Docker container
      }
    }
  }
  post {
    always {
      sh 'docker stop my-node-container' // Stop Docker container
      sh 'docker rm my-node-container'   // Remove Docker container
    }
  }
}
