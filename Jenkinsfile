pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from your Git repository
                checkout scm
            }
        }
        
        stage('Install Dependencies') {
            steps {
                // Install Node.js and npm
                sh 'curl -sL https://deb.nodesource.com/setup_14.x | sudo -E bash -'
                sh 'sudo apt-get install -y nodejs'

                // Install project dependencies
                sh 'npm install'
            }
        }

        stage('Run Tests') {
            steps {
                // Run WebDriverIO tests
                sh 'npx wdio run wdio.conf.js'
            }
        }
    }

    post {
        always {
            // Archive test reports
            junit '**/test-report.xml'
        }
    }
}
