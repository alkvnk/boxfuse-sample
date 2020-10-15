pipeline {
  agent {
    docker {
      image 'maven:3-openjdk-8'
    }
  }
  stages {
      stage ("Copy source from my git") {
          steps {
          git 'https://github.com/alkvnk/boxfuse-sample.git'
          }
      }
      stage ("build") {
          steps {
              sh "mvn package"
          }
      }
      stage ("Make docker image") {
            steps {
                deploy adapters: [tomcat8(credentialsId: '8345c766-af96-4891-9dea-304c6bcee514', path: '', url: 'http://130.193.49.193:8080/')], contextPath: 'webApp07', war: '**/*.war'
            }
      }
  }
}