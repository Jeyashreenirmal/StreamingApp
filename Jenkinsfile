
pipeline {
    agent any

    environment {
        AWS_REGION = 'us-east-1'
        AWS_ACCOUNT_ID = '975050024946'
        IMAGE_TAG = "${BUILD_NUMBER}"

        FRONTEND_REPO = 'my-app'
        ADMIN_REPO = 'backend-jsree'
        AUTH_REPO = 'backend2-jsree'
        CHAT_REPO = 'backend3-jsree'
        STREAMING_REPO = 'backend4-jsree'
    }

    stages {


        stage('Login to ECR') {
            steps {
                sh """
                aws ecr get-login-password --region $AWS_REGION | \
                docker login --username AWS --password-stdin \
                $AWS_ACCOUNT_ID.dkr.ecr.$AWS_REGION.amazonaws.com
                """
            }
        }

        // ================= FRONTEND =================

        stage('Build & Push Frontend') {
            steps {
                dir('frontend') {
                    sh """
                    docker build -t $FRONTEND_REPO:$IMAGE_TAG .
                    docker tag $FRONTEND_REPO:$IMAGE_TAG \
                    $AWS_ACCOUNT_ID.dkr.ecr.$AWS_REGION.amazonaws.com/$FRONTEND_REPO:$IMAGE_TAG
                    docker push \
                    $AWS_ACCOUNT_ID.dkr.ecr.$AWS_REGION.amazonaws.com/$FRONTEND_REPO:$IMAGE_TAG
                    """
                }
            }
        }

        // ================= AUTH =================

        stage('Build & Push Admin Service') {
            steps {
                dir('backend/adminService') {
                    sh """
                    docker build -t $ADMIN_REPO:$IMAGE_TAG .
                    docker tag $ADMIN_REPO:$IMAGE_TAG \
                    $AWS_ACCOUNT_ID.dkr.ecr.$AWS_REGION.amazonaws.com/$ADMIN_REPO:$IMAGE_TAG
                    docker push \
                    $AWS_ACCOUNT_ID.dkr.ecr.$AWS_REGION.amazonaws.com/$ADMIN_REPO:$IMAGE_TAG
                    """
                }
            }
        }

        // ================= USERS =================

        stage('Build & Push  auth Service') {
            steps {
                dir('backend/authService') {
                    sh """
                    docker build -t $AUTH_REPO:$IMAGE_TAG .
                    docker tag $AUTH_REPO:$IMAGE_TAG \
                    $AWS_ACCOUNT_ID.dkr.ecr.$AWS_REGION.amazonaws.com/$AUTH_REPO:$IMAGE_TAG
                    docker push \
                    $AWS_ACCOUNT_ID.dkr.ecr.$AWS_REGION.amazonaws.com/$AUTH_REPO:$IMAGE_TAG
                    """
                }
            }
        }

        // ================= MOVIES =================

        stage('Build & Push chat Service') {
            steps {
                dir('backend/chatService') {
                    sh """
                    docker build -t $CHAT_REPO:$IMAGE_TAG .
                    docker tag $CHAT_REPO:$IMAGE_TAG \
                    $AWS_ACCOUNT_ID.dkr.ecr.$AWS_REGION.amazonaws.com/$CHAT_REPO:$IMAGE_TAG
                    docker push \
                    $AWS_ACCOUNT_ID.dkr.ecr.$AWS_REGION.amazonaws.com/$CHAT_REPO:$IMAGE_TAG
                    """
                }
            }
        }

        // ================= PAYMENTS =================

        stage('Build & Push Streaming Service') {
            steps {
                dir('backend/streamingService') {
                    sh """
                    docker build -t $STREAMING_REPO:$IMAGE_TAG .
                    docker tag $STREAMING_REPO:$IMAGE_TAG \
                    $AWS_ACCOUNT_ID.dkr.ecr.$AWS_REGION.amazonaws.com/$STREAMING_REPO:$IMAGE_TAG
                    docker push \
                    $AWS_ACCOUNT_ID.dkr.ecr.$AWS_REGION.amazonaws.com/$STREAMING_REPO:$IMAGE_TAG
                    """
                }
            }
        }
    }

    post {
        success {
            echo "All images built and pushed successfully!"
        }
        failure {
            echo "Build failed. Check logs."
        }
    }
}
