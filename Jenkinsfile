pipeline {
    agent any
    tools{
        maven 'Maven3'
    }
    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from GitHub
                checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/pgnaik/MyWebApp.git']])
            }
        }

        stage('Build') {
            steps {
                // Navigate to the MyApp directory and run Maven build
                
                    bat 'mvn clean install -f MyApp/pom.xml'
                
            }
        }

        stage('Test') {
            steps {
                // Navigate to the MyApp directory and run Maven tests
                dir('MyApp') {
                    bat 'mvn test'
                }
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploying"
                // Navigate to the MyApp directory and deploy the application (example)
                // dir('MyApp') {
                //     bat 'mvn deploy' // Uncomment and configure as needed
                // }
            }
        }
    }

    post {
        

        success {
            echo 'Build succeeded!'
        }

        failure {
            echo 'Build failed!'
        }
    }
}
