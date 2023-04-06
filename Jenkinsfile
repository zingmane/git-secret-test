@Library('campudus-jenkins-shared-lib') _

pipeline {
  agent any

  options {
    timeout(time: 5, unit: 'MINUTES')
    ansiColor('xterm')
    timestamps()
  }

  stages {
    stage('Build') {
      steps {
        sh "echo setup/clean up stuff..."
        // remove images older than two weeks
        sh 'docker rmi -f $(docker images --filter "reference=campudus/rebike1-erp*" | grep " [weeks|months|years]* ago" | awk \'{print $3}\') 2>/dev/null || echo "No images to cleanup"'
        // delete older test networks
        echo "Environment variables are:"
        sh "printenv | sort"
        echo ""
        echo "Groovy/Pipeline variables are:"
        script {
            groovyVars = [:] << getBinding().getVariables()
            groovyVars.each  {k,v -> print "$k = $v"}
        }

        sh "ls -rtla"
        sh "cat .env"
      }
    }
  }
}
