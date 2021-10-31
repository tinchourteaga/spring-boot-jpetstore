pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        git(url: 'https://github.com/tinchourteaga/spring-boot-jpetstore.git', branch: 'master')
        withGradle() {
          sh '''./gradlew init
./gradlew build
./gradlew jar'''
        }

      }
    }

    stage('Test') {
      steps {
        sh './gradlew test'
      }
    }

    stage('Validate') {
      steps {
        sh './gradlew check'
      }
    }

    stage('Deploy') {
      steps {
        echo 'Deploying...'
      }
    }

    stage('Analyze') {
      steps {
        withGradle() {
          sh './gradlew sonarqube -Dsonar.projectKey=ing-sw-test -Dsonar.host.url=http://localhost:9000 -Dsonar.login=a658cdb2acd018b598b2e44e63c985e87a0376b6'
        }

      }
    }

  }
}