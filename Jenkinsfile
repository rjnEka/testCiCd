node {

    checkout scm

    env.DOCKER_API_VERSION="1.23"
    
    sh "git rev-parse --short HEAD > commit-id"

    tag = readFile('commit-id').replace("\n", "").replace("\r", "")
    appName = "hello-kenzan-CICD"
    registryHost = "10.0.2.15:31936/"
    imageName = "${registryHost}${appName}:${tag}"
    env.BUILDIMG=imageName
	
	stage "Test"
	    echo 'Testing..'	
}