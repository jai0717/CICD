pipeline {
    agent any
    stages {
        stage('Pull') {
            steps {
              //get some code from git repo
                git 'https://github.com/jai0717/war-web-project.git'
            }
        }
        stage('Sonar Test') {
            steps {
                bat "mvn sonar:sonar"
            }
        }
         stage('build') {
            steps {
                bat "mvn clean package"
            }
        }
            post {
                success {
                    junit '**/target/surefire-reports/TEST-*.xml'
                    archiveArtifacts '/target/*jar'
                }
            }
        }
        stage('Deliver') {
            steps {
                sh './jenkins/scripts/deliver.sh'
            }
        }
    }
}
