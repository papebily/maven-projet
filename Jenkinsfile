
pipeline {
    agent any
    stages {
        stage('Checkout Code ') {
            steps {
                // Get some code from a GitHub repository
             git branch: 'master', url: 'https://github.com/papebily/maven-projet.git'
            }
        }
        stage('Build Project') {
            steps {
                 // Run Maven on a Unix agent.
                sh "mvn clean package -DskipTests"
            }
        }
        stage('Test') {
            steps {
                 // Run Maven on a Unix agent.
                sh "mvn test"
            }
        }
        stage('Deploy') {
            steps {
                 // Run Maven on a Unix agent.
                echo "deploiement reussi"
            }
        }
    }
}

