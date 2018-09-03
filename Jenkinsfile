podTemplate(label: 'builder',
            containers: [
                    containerTemplate(name: 'kubectl', image: 'ceroic/kubectl', command: 'cat', ttyEnabled: true),
                    containerTemplate(name: 'maven', image: 'maven:3.3.9-jdk-8-alpine', ttyEnabled: true, command: 'cat')
            ]) {

        node('builder') {

            stage('Checkout') {
                checkout scm
            }

            stage('Build') {
                container('maven') {
                    sh 'mvn clean install'
                }
            }

            stage('Build docker image') {
               
                        sh "kubectl get pods"
                        
            }
        }
    }
