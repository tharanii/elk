pipeline {

  agent { label 'kubepod' }

  stages {

    stage('Checkout Source') {
      steps {
        git url:'https://github.com/tharanii/elk.git', branch:'master'
      }
    }
    stage('Deploy - logstash') {
      steps {
        script {
	  kubernetesDeploy(configs: "logstash.yaml", kubeconfigId: "mykubeconfig")
        }
      }
    }
    stage('Deploy - filebeat') {
      steps {
        script {
	  kubernetesDeploy(configs: "filebeat.yaml", kubeconfigId: "mykubeconfig")
        }
      }
    }
    stage('Deploy - metricbeats') {
      steps {
        script {
	  kubernetesDeploy(configs: "metricbeat.yaml", kubeconfigId: "mykubeconfig")
        }
      }
    }
    stage('Deploy - currator') {
      steps {
        script {
	  kubernetesDeploy(configs: "curator-cronjob.yaml", kubeconfigId: "mykubeconfig")
        }
      }
    }
  }

}
