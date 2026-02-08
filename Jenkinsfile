pipeline {
    agent any

    stages {
        stage('Checkout Source') {
            steps {
                checkout scm
            }
        }

        stage('Run Taurus Login Test') {
            steps {
                bat '''
                echo ==================================
                echo Running Taurus login test
                echo ==================================
                bzt taurus\\login_test.yml
                '''
            }
        }
    }

    post {
        always {
            archiveArtifacts artifacts: 'jmeter\\results\\**', fingerprint: true
        }
    }
}
