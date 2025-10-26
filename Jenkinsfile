pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/PetarPetrov24/SEDO_Regular-Exam-3'
            }
        }

        stage('Install Dependencies') {
            steps {
                bat 'pip install --upgrade pip'
                bat 'pip install -r requirements.txt'
            }
        }

        stage('Lint') {
            steps {
                bat 'pip install flake8'
                bat 'flake8 .'
            }
        }

        stage('Run Tests') {
            steps {
                bat 'pip install pytest'   // make sure pytest is installed
                bat 'pytest'
            }
        }
    }

    post {
        always {
            // optional: only if you generate JUnit XML test results
            // junit '**/test-results.xml'
        }
    }
}
