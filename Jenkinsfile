pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        echo 'This is a test'
        git(url: 'https://github.com/pfinnega/jenkinsblue', branch: 'master', changelog: true, poll: true, credentialsId: 'ae6ab6b0f6a1c9c60bc241b4459a729a07769ed2')
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
        fileExists 'test.log'
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