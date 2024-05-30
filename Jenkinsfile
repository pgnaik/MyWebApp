pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from GitHub
                git url: 'https://github.com/pgnaik/MyApp.git', branch: 'master'
            }
        }

        stage('Build') {
            steps {
                // Navigate to the MyApp directory and run Maven build
                dir('MyApp') {
                    bat 'mvn clean install'
                }
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
                // Navigate to the MyApp directory and deploy the application (example)
                // dir('MyApp') {
                //     bat 'mvn deploy' // Uncomment and configure as needed
                // }
            }
        }
    }

    post {
        always {
            // Archive artifacts from the MyApp directory
            archiveArtifacts artifacts: 'MyApp/target/*.war', allowEmptyArchive: true
            junit 'MyApp/target/surefire-reports/*.xml'
        }

        success {
            echo 'Build succeeded!'
        }

        failure {
            echo 'Build failed!'
        }
    }
}
