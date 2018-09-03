node {
	agent {
    kubernetes {
      label 'sample-app'
      defaultContainer 'jnlp'
      yaml """
apiVersion: v1
kind: Pod
metadata:
labels:
  component: ci
spec:
  # Use service account that can deploy to all namespaces
  serviceAccountName: cd-jenkins
  containers:
  - name: gcloud
    image: gcr.io/cloud-builders/gcloud
    command:
    - cat
    tty: true
  - name: kubectl
    image: gcr.io/cloud-builders/kubectl
    command:
    - cat
    tty: true
"""
}
  }
    checkout scm

    env.DOCKER_API_VERSION="1.23"
    
    sh "git rev-parse --short HEAD > commit-id"

    tag = readFile('commit-id').replace("\n", "").replace("\r", "")
    appName = "hello-kenzan-pipe"
    registryHost = "127.0.0.1:30400/"
    imageName = "${registryHost}${appName}:${tag}"
    env.BUILDIMG=imageName
	
    stage "Test"
	echo 'Testing..'
	echo 'End Testing..'
	
    stage "test2"
	echo'testing kubectl'
	sh "kubectl cluster-info"
   
}
