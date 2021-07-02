pipeline {
  agent any
    stages {
        stage('Build') {
            steps {
                sh "git pull origin main"
                sh "bash ./gradlew :spotlessApply"
   				sh 'bash ./gradlew clean build'
                sh "bash ./gradlew bootRun"
            }
        }
        stage('Test') {
            steps {
                sh "bash ./gradlew test"
            }
        }
        stage('Code coverage') {
            steps {
                sh "bash ./gradlew -i test jacocoTestReport"
            }
        }
         stage('Analyze') {
            steps {
                sh "bash ./gradlew sonarqube -Dsonar.projectKey=sonar.host.url -Dsonar.host.url=http://172.18.0.3:9000 -Dsonar.login=8ad9a11c2a13420c8fb144a5fc47e324"
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