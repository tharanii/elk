pipeline {

  agent { label 'kubepod' }

  stages {

    stage('Checkout Source') {
      steps {
        git url:'https://github.com/tharanii/elk.git', branch:'master'
      }
    }

    stage('Deploy App') {
      steps {
        script {
	  kubernetesDeploy(configs: "kibana.yaml", kubeconfigId: "mykubeconfig")
        }
      }
    }

  }

}
