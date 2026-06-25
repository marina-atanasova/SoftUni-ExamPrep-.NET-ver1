pipeline {
    agent any

    stages {

        stage('Restore') {
            when {
                anyOf {
                    branch 'main'
                    expression {
                        env.BRANCH_NAME?.startsWith('feature')
                    }
                }
            }

            steps {
                echo 'Restoring project...'
                sh 'dotnet restore'
            }
        }

        stage('Build') {
            when {
                anyOf {
                    branch 'main'
                    expression {
                        env.BRANCH_NAME?.startsWith('feature')
                    }
                }
            }

            steps {
                echo 'Building application...'
                sh 'dotnet build --configuration Release --no-restore'
            }
        }

        stage('Test') {
            when {
                anyOf {
                    branch 'main'
                    expression {
                        env.BRANCH_NAME?.startsWith('feature')
                    }
                }
            }

            steps {
                echo 'Running tests...'
                sh 'dotnet test --configuration Release --no-build'
            }
        }
    }
}
