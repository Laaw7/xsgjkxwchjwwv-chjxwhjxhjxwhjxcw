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
        stage("SonarQube") {
            steps {
                script {
                    withSonarQubeEnv('SonarQube_Local') {
                        sh 'mvn clean package sonar:sonar'
                    }
                }
            }
        }
    }
}
