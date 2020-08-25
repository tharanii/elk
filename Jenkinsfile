pipeline {

  agent { label 'kubepod' }

  stages {

    stage('Checkout Source') {
      steps {
        git url:'https://github.com/tharanii/elk.git', branch:'master'
      }
    }
    stage('Deploy elastic') {
      steps {
        script {
	  kubernetesDeploy(configs: "elasticsearch-ss.yaml", kubeconfigId: "mykubeconfig")
        }
      }
    }
  }
  
}
