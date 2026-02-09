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
                bzt perf_ci_cd_integration\\taurus\\login_test.yml
                '''
            }
        }
    }

    post {
        always {
            archiveArtifacts artifacts: 'perf_ci_cd_integration\\jmeter\\results\\**', fingerprint: true
        }
    }
}
