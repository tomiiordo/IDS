pipeline {
  agent any
    stages {
        stage('Build') {
            steps {
                sh "git pull origin main"
   				sh 'bash ./gradlew clean build'
                sh "bash ./gradlew bootRun"
            }
        }
        stage('Code coverage') {
            steps {
                withGradle {
                    sh './gradlew -i test jacocoTestReport'
                }
            }
        }
         stage('Analyze') {
            steps {
                withGradle {
                    sh './gradlew sonarqube -Dsonar.projectKey=sonar.host.url -Dsonar.host.url=http://localhost:9000 -Dsonar.login=8ad9a11c2a13420c8fb144a5fc47e324'
                }
            }
        }
        stage('Test') {
            steps {
                echo 'Testing...'
            }
        }
        stage('Validate') {
            steps {
                echo 'Validate....'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
		}
  }
}