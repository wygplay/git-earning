pipeline {
  agent any
  parameters {
      string(name: 'ITEMUSER', defaultValue: 'wyg', description: '以什么环境用户执行此次构建？')
      string(name: 'BRANCH', defaultValue: 'master', description: '使用什么分支用于此次构建？')
  }
  stages {
    stage('pull') {
      steps {
        dir(path: "./") {
          git(url: "https://github.com/wygplay/git-learning.git")
        }
      }
    }
    stage('deployment') {
      steps {
        dir(path: './') {
          ansiblePlaybook(playbook: "./ansible/${ITEMNAME}.yaml", disableHostKeyChecking: true, extras: '--extra-vars \'{"src_dir":"${WORKSPACE}/${ITEMNAME}"}\'', colorized: true, inventory: "./ansible/inventory/${params.ITEMUSER}")
        }
      }
    }
  }
  environment {
    ITEMNAME = 'git-learning'
  }
  
}
