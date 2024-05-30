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
                echo "Deploying to Tomcat Container" 
                deploy adapters: [tomcat9(credentialsId: '9aa5ca8b-299a-4710-9c4c-9c43833ac983', path: '', url: 'http://localhost:9000')], contextPath: null, war: '**/*.war'
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
