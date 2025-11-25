pipeline {
    agent any

    tools {
        jdk 'jdk17'       // Name must match JDK in Jenkins tools
        maven 'maven3'    // Name must match Maven in Jenkins tools
    }

    triggers {
        // Build when GitHub sends a push event
        githubPush()
   

    stages
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build with Maven') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Archive JAR') {
            steps {
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            }
        }
    }
}
