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
    
    stage "Build"
       echo 'Building..'
        sh "docker build -t ${imageName} hello-kenzan/"
    
    stage "Push"
	echo 'Pushing..'
        sh "docker push ${imageName}"
    
    stage "Deploy"
        echo 'Deploying..'
        sh "sed 's#__IMAGE__#'$BUILDIMG'#' hello-kenzan/k8s/deployment.yaml | kubectl apply -f -"
}
