node('master') {
  stage('Unit Tests') {
    git url: "https://github.com/bobbydeveaux/micro-rmq.git"
  }
  stage('Build Image') {
    sh "oc start-build rmq --from-file=. --follow"
  }
  stage('Deploy') {
    openshiftDeploy depCfg: 'rmq', namespace: 'fbac'
    openshiftVerifyDeployment depCfg: 'rmq', replicaCount: 1, verifyReplicaCount: true
  }
}