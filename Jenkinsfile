pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        git(url: 'https://github.com/tinchourteaga/spring-boot-jpetstore.git', branch: 'master')
        withGradle() {
          sh '''\'./gradlew init\'
\'./gradlew build\''''
        }

      }
    }

    stage('Test') {
      steps {
        sh '\'./gradlew test\''
      }
    }

    stage('Validate') {
      steps {
        sh '\'./gradlew check\''
      }
    }

    stage('Deploy') {
      steps {
        echo 'Deploying...'
      }
    }

  }
}