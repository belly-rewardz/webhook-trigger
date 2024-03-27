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
          script {
            echo "hello world 2"
            echo "hello world 3"
            echo "hello world 4"
            echo "hello world 5"
            echo "hello world 6"
            echo "hello world 7"
            echo "hello world 8"
            echo "hello world 9"
            echo "hello world 10"
            echo "hello world 11"
            }
        }
      }
    }
  }
}
