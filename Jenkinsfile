pipeline {
    agent any
    environment {
        SONAR_QUBE_URL = 'http://localhost:9000'
        SONAR_QUBE_TOKEN = '61be11f80610bcb5d747318260a416d4fbd3b6d9'
    }
    stages {
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('SONAR_LOCAL') {
                    sh "${tool 'SONAR_SCANNER'}/bin/sonar-scanner -Dsonar.projectKey=lab-jenkins-api -Dsonar.host.url=${env.SONAR_QUBE_URL} -Dsonar.login=${env.SONAR_QUBE_TOKEN} -Dsonar.java.binaries=./"
                }
            }
        }
        stage('Deploy') {
            steps {
                sh 'mvn clean package'
            }
        }
    }
}
