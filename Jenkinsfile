pipeline {
    agent any
    tools {
        maven 'maven'
    }
    stages {
        stage("build") {
            steps {
                sh 'mvn -v'
            }
        }
        stage("test") {
            steps {
                echo 'Running tests'
            }
        }
        stage("deploy") {
            steps {
                echo 'Deploying application'
            }
        }
        stage("Build & Analyse avec SonarQube") {
            agent any
            steps {
                script {
                    sh 'mvn clean package sonar:sonar'
                }
            }
        }
    }
}
