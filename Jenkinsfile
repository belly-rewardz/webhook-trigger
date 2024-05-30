void setBuildStatus(String message, String state) {
  step([
      $class: "GitHubCommitStatusSetter",
      reposSource: [$class: "ManuallyEnteredRepositorySource", url: "https://github.com/belly-rewardz/webhook-trigger"],
      contextSource: [$class: "ManuallyEnteredCommitContextSource", context: "ci/jenkins/build-status"],
      errorHandlers: [[$class: "ChangingBuildStatusErrorHandler", result: "UNSTABLE"]],
      statusResultSource: [ $class: "ConditionalStatusResultSource", results: [[$class: "AnyBuildResult", message: message, state: state]] ]
  ]);
}

pipeline {
  agent {
    kubernetes {
      yaml '''
apiVersion: v1
kind: Pod
spec:
  containers:
  - name: node
    image: node:14.17.2
    command: ["/bin/sh"]
    args: ["-c", "while true; do echo hello; sleep 10;done"]
  serviceAccountName: analytics-sa
'''
      }
    }
options {
  ansiColor('xterm')
  buildDiscarder logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '25', daysToKeepStr: '', numToKeepStr: '25')
}

  stages {
    stage('Echo') {
      steps {
        container('node') {
          setBuildStatus("Build in progress", "PENDING");
          script {
            echo "hello world 2"
            sh "ls -lah"
            sh "pwd || true"
            }
        }
      }
    }
  }
  post {
    success {
        setBuildStatus("Build succeeded", "SUCCESS");
    }
    failure {
        setBuildStatus("Build failed", "FAILURE");
    }
  }
}
