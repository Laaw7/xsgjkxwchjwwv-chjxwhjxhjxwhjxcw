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
         stage('Dependency-Check') {
            steps {
                // Lancer l'analyse des dépendances OWASP
                dependencyCheck additionalArguments: '''
                    -o './'
                    -s './'
                    -f 'ALL'
                    --prettyPrint''', 
                    odcInstallation: 'owasp-dependency'
                dependencyCheckPublisher pattern: 'dependency-check-report.xml'
            }
        }
    }
}