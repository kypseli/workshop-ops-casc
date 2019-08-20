pipeline {
  agent { label 'master' }
  stages {
    stage('reload jcasc') {
      when { 
        branch 'master'
      }
      steps {
        echo "preparing to reload "
        echo "preparing Jenkins CLI"
        sh 'curl -O http://teams-ops.cje.svc.cluster.local/teams-ops/jnlpJars/jenkins-cli.jar'
        withCredentials([usernamePassword(credentialsId: 'cli-username-token', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
          sh """
            alias cli='java -jar jenkins-cli.jar -s \'http://teams-ops.cje.svc.cluster.local/teams-ops/\' -auth $USERNAME:$PASSWORD'
            cli reload-jcasc-configuration
          """
        }
      }
    }
  }
}
