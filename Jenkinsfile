pipeline {
    agent any  // Use any available agent

    tools {
        // Ensure this matches the name configured in Jenkins
        jdk 'JDK8'
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/chinmayiii/maventogradvedio.git'
            }
        }

        stage('Build') {
            steps {

                sh 'chmod +x gradlew'
                sh './gradlew build'  // Run Maven build
            }
        }

       stage('Test') {
           steps {
               sh './gradlew test'  // Run unit tests
           }
        }

              
        stage('Run Application') {
            steps {
                // Start the JAR application
                sh './gradlew run'
            }
        }

        
    }

    post {
        success {
            echo 'Build and deployment successful!'
        }
        failure {
            echo 'Build failed!'
        }
    }
}
