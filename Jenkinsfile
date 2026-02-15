pipeline {
  agent any

  stages {

    stage('Checkout') {
      steps {
        git branch: 'main',
            url: 'https://github.com/Jeyashreenirmal/StreamingApp.git',
            credentialsId: 'github-tokenjsree'
      }
    }

    stage('Login to AWS ECR') {
      steps {
        withCredentials([[
          $class: 'AmazonWebServicesCredentialsBinding',
          credentialsId: 'aws-credentials'
        ]]) {
          sh '''
            aws ecr get-login-password --region us-east-1 | \
            docker login --username AWS --password-stdin \
            975050024946.dkr.ecr.us-east-1.amazonaws.com
          '''
        }
      }
    }

    // ================= FRONTEND =================
    stage('Build & Push Frontend') {
      steps {
        dir('frontend') {
          sh '''
            docker build -t my-app:latest .
            docker tag my-app:latest 975050024946.dkr.ecr.us-east-1.amazonaws.com/my-app:latest
            docker push 975050024946.dkr.ecr.us-east-1.amazonaws.com/my-app:latest
          '''
        }
      }
    }

    // ================= ADMIN SERVICE =================
    stage('Build & Push Admin Service') {
      steps {
        dir('backend/adminService') {
          sh '''
            docker build -t backend-jsree:admin .
            docker tag backend-jsree:admin 975050024946.dkr.ecr.us-east-1.amazonaws.com/backend-jsree:admin
            docker push 975050024946.dkr.ecr.us-east-1.amazonaws.com/backend-jsree:admin
          '''
        }
      }
    }

    // ================= AUTH SERVICE =================
    stage('Build & Push Auth Service') {
      steps {
        dir('backend/authService') {
          sh '''
            docker build -t backend2-jsree:auth .
            docker tag backend2-jsree:auth 975050024946.dkr.ecr.us-east-1.amazonaws.com/backend2-jsree:auth
            docker push 975050024946.dkr.ecr.us-east-1.amazonaws.com/backend2-jsree:auth
          '''
        }
      }
    }

    // ================= CHAT SERVICE =================
    stage('Build & Push Chat Service') {
      steps {
        dir('backend/chatService') {
          sh '''
            docker build -t backend3-jsree:chat .
            docker tag backend3-jsree:chat 975050024946.dkr.ecr.us-east-1.amazonaws.com/backend3-jsree:chat
            docker push 975050024946.dkr.ecr.us-east-1.amazonaws.com/backend3-jsree:chat
          '''
        }
      }
    }

    // ================= STREAMING SERVICE =================
    stage('Build & Push Streaming Service') {
      steps {
        dir('backend/streamingService') {
          sh '''
            docker build -t backend4-jsree:streaming .
            docker tag backend4-jsree:streaming 975050024946.dkr.ecr.us-east-1.amazonaws.com/backend4-jsree:streaming
            docker push 975050024946.dkr.ecr.us-east-1.amazonaws.com/backend4-jsree:streaming
          '''
        }
      }
    }
  }

  post {
    success {
      echo '✅ All services built and pushed successfully'
    }
    failure {
      echo '❌ Pipeline failed'
    }
  }
}