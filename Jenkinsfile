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
                bat 'python -m pip install --upgrade pip'
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
                bat 'pip install pytest'
                bat 'pytest'
            }
        }
    }

    post {
        always {
            echo "Pipeline finished."   // no 'steps' block here
        }
    }
}
