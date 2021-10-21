pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        git(url: 'https://github.com/tinchourteaga/spring-boot-jpetstore.git', branch: 'master')
        withGradle() {
          sh '''sh \'./gradlew init\'
sh \'./gradlew build\''''
        }

      }
    }

    stage('Test') {
      steps {
        sh 'sh \'./gradlew test\''
      }
    }

    stage('Validate') {
      steps {
        sh 'sh \'./gradlew check\''
      }
    }

    stage('Deploy') {
      steps {
        echo 'Deploying...'
      }
    }

  }
}