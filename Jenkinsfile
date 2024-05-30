// void setBuildStatus(String message, String state) {
//   step([
//       $class: "GitHubCommitStatusSetter",
//       reposSource: [$class: "ManuallyEnteredRepositorySource", url: "https://github.com/belly-rewardz/webhook-trigger"],
//       contextSource: [$class: "ManuallyEnteredCommitContextSource", context: "ci/jenkins/build-status"],
//       errorHandlers: [[$class: "ChangingBuildStatusErrorHandler", result: "UNSTABLE"]],
//       statusResultSource: [ $class: "ConditionalStatusResultSource", results: [[$class: "AnyBuildResult", message: message, state: state]] ]
//   ]);
// }

pipeline {
  agent {
        label 'master'
    }
options {
  ansiColor('xterm')
  buildDiscarder logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '25', daysToKeepStr: '', numToKeepStr: '25')
}

  stages {
    stage('Echo') {
      steps {
        // setBuildStatus("Build in progress", "PENDING");
        script {
          echo "hello world"
          sh "ls -lah"
          sh "pwd || true"
          }
      }
    }
  }
  // post {
  //   success {
  //       setBuildStatus("Build succeeded", "SUCCESS");
  //   }
  //   failure {
  //       setBuildStatus("Build failed", "FAILURE");
  //   }
  // }
}
