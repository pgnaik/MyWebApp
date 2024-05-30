pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from GitHub
                git url: 'https://github.com/pgnaik/MyWebApp.git', branch: 'master'
            }
        }

        stage('Build') {
            steps {
                // Build the Maven project
                bat 'mvn clean install'
            }
        }

        stage('Test') {
            steps {
                // Run tests
                bat 'mvn test'
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploying the application..."
                // sh 'mvn deploy' // Uncomment and configure as needed
            }
        }
    }

    post {
        always {
            // Clean up and archive artifacts
            archiveArtifacts artifacts: '**/target/*.jar', allowEmptyArchive: true
            junit 'target/surefire-reports/*.xml'
        }

        success {
            echo 'Build succeeded!'
        }

        failure {
            echo 'Build failed!'
        }
    }
}
