def isTargetBranch() {
    return env.BRANCH_NAME == 'main' || env.BRANCH_NAME == 'feature/**'
}

pipeline {
    agent any

    stages {
        stage('Restore Dependencies') {
            when {
                expression { isTargetBranch() }
            }
            steps {
                bat 'dotnet restore'
            }
        }

        stage('Build Project') {
            when {
                expression { isTargetBranch() }
            }
            steps {
                bat 'dotnet build --configuration Release'
            }
        }

        stage('Run dotnet tests') {
            when {
                expression { isTargetBranch() }
            }
            steps {
                bat 'dotnet test'
            }
        }
    }
}