pipeline {
  agent any
  stages {
    stage('检出 GitHub') {
      steps {
        checkout([
          $class: 'GitSCM',
          branches: [[name: env.GIT_BUILD_REF]], 
          userRemoteConfigs: [[url: env.GIT_REPO_URL, credentialsId: env.CREDENTIALS_ID]]
        ])
      }
    }
    stage('推送到 CODING') {
      steps {
        sh "git push https://${PROJECT_TOKEN_GK}:${PROJECT_TOKEN}@e.coding.net/graytoowolf/graytoowolf/plugins-dist.git HEAD:master"
      }
    }
  }
}