pipeline {
    agent any // Runs on any available agent

    tools {
        maven 'Maven_m' // Matches the name configured in Global Tool Configuration
    }

    stages {
        stage('Build') {
            steps {
                // Run Maven clean and compile
                sh 'mvn clean compile'
            }
        }
        stage('Test') {
            steps {
                // Run Maven tests
                sh 'mvn test'
            }
        }
    }

    post {
        always {
            // Archive test results and artifacts
            junit '**/target/surefire-reports/*.xml'
            archiveArtifacts artifacts: '**/target/*.jar', allowEmptyArchive: true
        }
    }
}
