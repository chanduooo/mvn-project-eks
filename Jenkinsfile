pipeline {
    agent any

    stages {
        stage('mvn build') {
            steps {
                sh 'mvn clean package'
            }
        }
         stage('junit') {
            steps {
                junit allowEmptyResults: true, testResults: 'target/test-reports/*.xml'
            }
        }
         stage('fingerprint') {
            steps {
                fingerprint 'target/*.jar'
          }
        }
         stage('archive artifact') {
            steps {
                archiveArtifacts artifacts: 'target/*.jar', followSymlinks: false
         }
    }
    post{
	always{
		cleanWs()
	}
     }    
  }
}
