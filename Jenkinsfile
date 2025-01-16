pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                // Get code from GitHub repository
                git branch: 'master', 
                    url: 'https://github.com/NikhilCyberk/basic-react-app.git'
            }
        }
        
        stage('Install') {
            steps {
                // Install Node dependencies
                bat 'npm install'
            }
        }
        
        stage('Test') {
            steps {
                // Run tests without watch mode
                bat 'npm test -- --watchAll=false'
            }
        }
        
        stage('Build') {
            steps {
                // Create production build
                bat 'npm run build'
            }
        }
        
        stage('Deploy') {
            steps {
                // Deploy to local folder
                bat '''
                    if not exist "C:\\Users\\nikhi\\Desktop\\Nexturn\\Module_Assignment\\Nexturn_Modules\\M6_Cloud\\01_Jenkins\\ex4\\Deploy\\react-app" mkdir "C:\\Users\\nikhi\\Desktop\\Nexturn\\Module_Assignment\\Nexturn_Modules\\M6_Cloud\\01_Jenkins\\ex4\\Deploy\\react-app"
                    xcopy /s /e /y "build\\*" "C:\\Users\\nikhi\\Desktop\\Nexturn\\Module_Assignment\\Nexturn_Modules\\M6_Cloud\\01_Jenkins\\ex4\\Deploy\\react-app"
                '''
            }
        }
    }
    
    post {
        success {
            echo 'Build and deployment successful!'
        }
        failure {
            echo 'Build or deployment failed!'
        }
    }
}