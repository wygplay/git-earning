pipeline {
  # agent关键字声明jenkins平台的哪个节点执行任务构建（当前架构中只有单台master节点），any指任意一台可用节点（当前架构中确定指向master节点）
  agent any
  # 参数化构建，用于在上线正式环境后能在不修改脚本的情况下改变构建用户和分支
  parameters {
      string(name: 'ITEMUSER', defaultValue: 'zjtest', description: '以什么环境用户执行此次构建？')
      string(name: 'BRANCH', defaultValue: 'feature-main', description: '使用什么分支用于此次构建？')
  }
  # stages声明包含多个stage
  stages {
    # stage关键字代表单个自动化的业务场景，如'pull'是一个stage,'deployment'是第二个stage
    stage('pull') {
      # steps声明包含多个step，此处包含git这一个step
      steps {
        # 基于当前jenkins pipeline的工作空间根目录即${WORKSPACE}在./develop目录执行（若该目录不存在则创建）
        dir(path: "./${ITEMNAME}") {
          # 执行git命令
          git(url: "https://github.com/wygplay/git-learning.git")
        }
      }
    }
  }
  environment {
    ITEMNAME = 'git-learning'
  }     
}
