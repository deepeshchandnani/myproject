pipeline {
  agent any
  stages {
    stage('Checkout & Run') {
      steps {
        sh 'chmod +x hello.sh'
        sh './hello.sh | tee build_output.txt'
      }
    }
  }
  post {
    always {
      emailext (
        subject: "Build: ${env.JOB_NAME} #${env.BUILD_NUMBER} - ${currentBuild.currentResult}",
        to: "recipient@example.com",
        body: "Status: ${currentBuild.currentResult}\\nSee console: ${env.BUILD_URL}console\\nLast lines:\\n${BUILD_LOG, maxLines=200}",
        attachLog: true
      )
    }
  }
}
