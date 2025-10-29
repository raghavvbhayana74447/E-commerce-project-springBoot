pipeline {
    agent any

    tools {
        maven 'maven'             
        jdk 'JDK17'              
    }

    environment {
        SONARQUBE_ENV = 'sonarqube'  
    }
   
    stages {
        stage('Checkout') {
            steps {
                git branch: 'master2', url: 'https://github.com/raghavvbhayana74447/E-commerce-project-springBoot.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('SonarQube Analysis') {
            steps {
                script {
                def scannerHome = tool 'sonarscanner' 
                withSonarQubeEnv("${SONARQUBE_ENV}") {
                sh "${scannerHome}/bin/sonar-scanner"
                }
                }
            }
        }

    }
}
