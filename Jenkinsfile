pipeline {
    agent any // Runs on any available agent

    tools {
        maven 'Maven' // Matches the name configured in Global Tool Configuration
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
            sh 'ls -la target/surefire-reports' // Debugging step
            // Archive test results and artifacts
            junit 'target/surefire-reports/*.xml'
            archiveArtifacts artifacts: '**/target/*.jar', allowEmptyArchive: true
        }
    }
}
