pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        step([$class: 'WsCleanup'])
        echo 'This is a test'
        
      }
    }
    stage('deploy') {
      steps {
        echo 'This is a test'
        writeFile(file: 'work.out', text: 'stuff')
      }
    }
    stage('test') {
      steps {
        fileExists 'work.out'
      }
    }
  }
  post {
    always {
      echo 'This will always run'
      archiveArtifacts '*.log'
      
    }
    
    success {
      echo 'This will run only if successful'
      
    }
    
    failure {
      echo 'This will run only if failed'
      archiveArtifacts '*.out'
      
    }
    
    unstable {
      echo 'This will run only if the run was marked as unstable'
      
    }
    
    changed {
      echo 'This will run only if the state of the Pipeline has changed'
      echo 'For example, if the Pipeline was previously failing but is now successful'
      
    }
    
  }
}
