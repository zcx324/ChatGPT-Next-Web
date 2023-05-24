pipeline {
  agent {
    node {
      label 'jenkins-node1'
    }

  }
  stages {
    stage('') {
      steps {
        sh '''#!/bin/bash


IMAGE_NAME="mosdns"
IMAGE_VERSION=$(date +\'%Y%m%d%H%M%S\')
REGISTRY_HOST="harbor.atstudy.com"
REGISTRY_NAMESPACE="test"
REGISTRY_USERNAME="admin"
REGISTRY_PASSWORD="51testing.bwf"
SSH_HOST="172.16.69.5"
SSH_USER="root"
SSH_PASSWORD="vncpassword"


docker build -t $IMAGE_NAME:$IMAGE_VERSION .
docker login $REGISTRY_HOST -u $REGISTRY_USERNAME -p $REGISTRY_PASSWORD

docker tag $IMAGE_NAME:$IMAGE_VERSION $REGISTRY_HOST/$REGISTRY_NAMESPACE/$IMAGE_NAME:$IMAGE_VERSION
docker push $REGISTRY_HOST/$REGISTRY_NAMESPACE/$IMAGE_NAME:$IMAGE_VERSION
docker tag $IMAGE_NAME:$IMAGE_VERSION $REGISTRY_HOST/$REGISTRY_NAMESPACE/$IMAGE_NAME:latest
docker push $REGISTRY_HOST/$REGISTRY_NAMESPACE/$IMAGE_NAME:latest


#sshpass -p $SSH_PASSWORD ssh $SSH_USER@$SSH_HOST -o StrictHostKeychecking=no "docker pull $REGISTRY_HOST/$REGISTRY_NAMESPACE/$IMAGE_NAME:$IMAGE_VERSION && docker run -d $REGISTRY_HOST/$REGISTRY_NAMESPACE/$IMAGE_NAME:$IMAGE_VERSION"'''
      }
    }

  }
}