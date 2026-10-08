pipeline {
    agent any
    tools {
        maven 'Maven3'
    }
    stages {
        stage('Checkout') {
            steps {
                // Pulls all tracking files directly from your repository
                checkout scmGit(
                    branches: [[name: '*/main']], 
                    extensions: [], 
                    userRemoteConfigs: [[url: 'https://github.com']]
                )
            }
        }
        stage('Package') {
            steps {
                // Compiles and compresses the app into a JAR file
                bat 'mvn clean package'
            }
        }
        stage('Run JAR') {
            steps {
                // Executes the generated JAR file directly out of the target directory
                bat 'java -cp target\\maven-package-demo-1.0.jar com.example.App'
            }
        }
    }
}
