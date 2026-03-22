pipeline {
    agent any
    tools {
        jdk 'JDK'  // your existing JDK
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/chinmayiii/maventogradvedio.git'
            }
        }

        stage('Build') {
            steps {
                script {
                    def gradleHome = tool 'Gradle7'
                    sh "${gradleHome}/bin/gradle build"
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    def gradleHome = tool 'Gradle7'
                    sh "${gradleHome}/bin/gradle test"
                }
            }
        }

        stage('Run Application') {
            steps {
                script {
                    def gradleHome = tool 'Gradle7'
                    sh "${gradleHome}/bin/gradle run"
                }
            }
        }
    }

    post {
        success { echo 'Build and deployment successful!' }
        failure { echo 'Build failed!' }
    }
}
