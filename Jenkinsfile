node {

    checkout scm

    env.DOCKER_API_VERSION="1.23"
    
    sh "git rev-parse --short HEAD > commit-id"

    tag = readFile('commit-id').replace("\n", "").replace("\r", "")
    appName = "hello-kenzan-CICD"
    registryHost = "10.0.2.15:31936/"
    imageName = "${registryHost}${appName}:${tag}"
    env.BUILDIMG=imageName

    stage "Build"
    
        sh "docker build -t ${imageName} hello-kenzan/"
    
    stage "Push"

        sh "docker push ${imageName}"

    stage "Deploy"

        sh "sed 's#__IMAGE__#'$BUILDIMG'#' hello-kenzan/k8s/deployment.yaml | kubectl apply -f -"
}