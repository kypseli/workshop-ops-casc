node('master') {
  echo "preparing to reload "
  checkout scm
  echo "preparing Jenkins CLI"
  sh 'curl -O http://team-ops/team-ops/jnlpJars/jenkins-cli.jar'
  withCredentials([usernamePassword(credentialsId: 'beedemo-admin-jenkins-api-key', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
    sh """
      alias cli='java -jar jenkins-cli.jar -s \'http://team-ops/team-ops/\' -auth $USERNAME:$PASSWORD'
      cli reload-jcasc-configuration
    """
  }
}
