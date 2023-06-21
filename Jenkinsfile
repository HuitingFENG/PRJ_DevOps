pipeline {
    agent any
    
    tools {nodejs "node"}
    
    stages {
        stage('Check Location') {
            steps {
                sh 'hostname'
            }
        }
        stage('Clone and install dependencies') {
            steps {
                git 'https://github.com/HuitingFENG/PRJ_DevOps.git'
                sh 'echo "Cloning and installing dependencies"'
                // nodesjs version is 12.18.0 (using the version in 2020 by following the youtube video)
                sh 'npm install'
            }
        }
        stage('Build') {
            steps {
                sh 'echo "Building"'
                sh 'npm run build'
            }
        }
        stage('Test') {
            steps {
                sh 'echo "Testing"'
                // Run the test script in the package.json file
                sh 'npm run test'
            }
        }
        stage('Deploy') {
            steps {
                sh 'echo "Deploying"'
                // Copy the build output to a directory on the same machine
                sh '''
                    mkdir -p deployment/directory
                    cp -r build/* deployment/directory
                '''
            }
        }
    }
}