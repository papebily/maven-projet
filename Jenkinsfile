
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
        /*stage('Deploy') {
            steps {
                 // Run Maven on a Unix agent.
                echo "deploiement reussi"
            }
        }*/
         stage('SonarQube Analysis') {
            steps {
                // Execute SonarQube analysis
                script {
                    def scannerHome = tool 'sonar_scanner_tool'
                    withSonarQubeEnv('sonarqubeserver') {
                        sh "${scannerHome}/bin/sonar-scanner -Dsonar.projectKey=vprofile \
                        -Dsonar.java.binaries=target/test-classes/com/visualpathit/account/controllerTest/"
                    }
                }
            }
        }
        stage("Quality Gate") {
            steps {
              timeout(time: 3, unit: 'MINUTES') {
                waitForQualityGate abortPipeline: true
              }
            }
        }    
    }
}

