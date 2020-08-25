pipeline {

  agent { label 'kubepod' }

  stages {

    stage('Checkout Source') {
      steps {
        git url:'https://github.com/tharanii/elk.git', branch:'master'
      }
    }

    stage('Deploy Elastic') {
      steps {
        script {
	  kubernetesDeploy(configs: "elasticsearch.yaml", kubeconfigId: "mykubeconfig")
        }
      }
    }
    stage('Deploy kibana') {
      steps {
        script {
	  kubernetesDeploy(configs: "kibana.yaml", kubeconfigId: "mykubeconfig")
        }
      }
    }
    stage('Deploy logstash') {
      steps {
        script {
	  kubernetesDeploy(configs: "logstash.yaml", kubeconfigId: "mykubeconfig")
        }
      }
    }

  }

}
