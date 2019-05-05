pipeline {
  agent any
  parameters {
      string(name: 'ITEMUSER', defaultValue: 'zjtest', description: '以什么环境用户执行此次构建？')
      string(name: 'BRANCH', defaultValue: 'feature-main', description: '使用什么分支用于此次构建？')
  }
  stages {
    stage('pull') {
      steps {
        dir(path: "./${ITEMNAME}") {
          git(url: "https://github.com/wygplay/git-learning.git")
        }
      }
    }
  }
  environment {
    ITEMNAME = 'git-learning'
  }     
}
