node {

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
    
    stage "Build"
        echo 'Building..'
        sh "docker build -t ${imageName} hello-kenzan/"
	echo 'End Building..'
    
    stage "Push"
	echo 'Pushing..'
        sh "docker push ${imageName}"
	echo 'End Pushing..'
	
    
    stage "Deploy"
        echo 'Deploying..'
	sh "kubectl config view"
	
	echo 'End Deploying..'
}
