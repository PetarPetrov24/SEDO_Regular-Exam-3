pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/PetarPetrov24/SEDO_Regular-Exam-3'
            }
        }

        stage('Restore Dependencies') {
            steps {
                // Restores all NuGet packages
                bat 'dotnet restore'
            }
        }

        stage('Build') {
            steps {
                bat 'dotnet build --no-restore'
            }
        }

        stage('Lint / Code Analysis') {
            steps {
                // Optional: use dotnet format for linting
                bat 'dotnet tool install -g dotnet-format || echo "Already installed"'
                bat 'dotnet format --verify-no-changes'
            }
        }

        stage('Run Tests') {
            steps {
                bat 'dotnet test --logger "trx;LogFileName=test-results.trx"'
            }
        }
    }

    post {
        always {
            echo "Pipeline finished."
        }
    }
}
