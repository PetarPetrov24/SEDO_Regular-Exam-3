pipeline {
    agent any  // run on any available Jenkins agent

    triggers {
        pollSCM('* * * * *')  // optional: polls Git repo every minute; for webhooks you can skip this
    }

    stages {
        stage('Checkout') {
            steps {
                // Clone repo and checkout main branch
                git branch: 'main', url: 'https://github.com/PetarPetrov24/SEDO_Regular-Exam-3'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'python -m venv venv'
                sh './venv/bin/pip install --upgrade pip'
                sh './venv/bin/pip install -r requirements.txt'
            }
        }

        stage('Lint') {
            steps {
                sh './venv/bin/flake8 .'
            }
        }

        stage('Run Tests') {
            steps {
                sh './venv/bin/pytest'
            }
        }
    }

    post {
        always {
            junit '**/test-results.xml'  // optional: if using JUnit-style test results
        }
    }
}
