pipeline {
  agent any

  parameters {
      string(name: "REPO_URL", description: "the url of repo, like `longguikeji/arkid-core`")
      string(name: "REPO_TYPE", description: "the type of the repo, like `ts` or `python`")
  }

  environment {
      GITHUB_ACCOUNT = credentials('devops-longguikeji-github-token') 
  }

  stages {
      stage('pre') {
          steps{
              sendDingTalk("pending", "开始构建")
          }
      }
      stage("init repo ci configure") {
          steps {
              sh "./ci_init ${REPO_URL} ${REPO_TYPE} ${GITHUB_ACCOUNT_PSW}"
          }
      }
  }
  post {
      success {
          sendDingTalk("success", "构建成功")
      }
      failure {
          sendDingTalk("failure", "构建失败")
      }
  }
}

def sendDingTalk(status, message) {
    if (status == "success") {
        img="https://s2.ax1x.com/2019/10/17/KEFSWd.png"
    } else if (status == "failure") {
        img="https://s2.ax1x.com/2019/10/17/KEFCQI.png"
    } else if (status == "pending") {
        img="https://s2.ax1x.com/2019/10/17/KEFkef.gif"
    } else {
        img=""
    }
    dingTalk([
        accessToken: "${env.DING_TALK_ENTRYPOINT}",
        jenkinsUrl: "${env.JENKINS_URL}",
        imageUrl: img,
        message: message,
    ])
}