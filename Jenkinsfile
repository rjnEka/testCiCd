podTemplate(label: 'jnlp', containers: [
    containerTemplate(
          name: 'jnlp',
          image: 'eggsy84/gcp-jenkins-slave-k8s-seed:latest',
          ttyEnabled: false,
          command: '',
          privileged: true,
          alwaysPullImage: false,
          workingDir: '/home/jenkins',
          args: '${computer.jnlpmac} ${computer.name}'
        )
    ]
)

{

  node('jnlp') {

      echo "hello world"
  }
}
