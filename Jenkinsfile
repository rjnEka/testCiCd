node {
    stage('List pods') {
    withKubeConfig(caCertificate: '', contextName: '', credentialsId: '902dbf82-3a09-46a5-8f13-af491662cd7a', serverUrl: '') {
   sh 'kubectl get pods'
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
