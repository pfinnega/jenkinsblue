pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        //step([$class: 'WsCleanup'])
        echo 'Building test ...'
      }
    }
    stage('deploy') {
      steps {
        echo 'Deploy ...'
        writeFile(file: 'work.out', text: 'stuff')
      }
    }
    stage('test') {
      steps {
        //fileExists 'work.out'
        echo "Testing ..."
      }
    }
    stage('Post') {
      steps {
        echo "Post install ..."
      }
    }
    
  }
  post {
    always {
      echo 'This will always run'
      
    }
    
    success {
      echo 'This will run only if successful'
      properties([pipelineTriggers([cron('H 23 * * *')])])
      build job: 'ust_install_sim'
      
    }
    
    failure {
      echo 'This will run only if failed'
      
    }
    
    unstable {
      echo 'This will run only if the run was marked as unstable'
      
    }
    
    changed {
      echo 'This will run only if the state of the Pipeline has changed'
      
    }
  }
}
