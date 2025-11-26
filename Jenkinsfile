pipeline {
    agent any
    tools {
        maven 'M3'
        jdk 'jdk21'
    }
    options {
        skipStagesAfterUnstable()
    }
    stages {
        //stage('Git Checkout') {
        //    steps {
        //        script {
        //            git branch: 'main', url: 'https://github.com/jessoussi/authentication-service/'
        //        }
        //    }
        //}
        stage ('Build') {
            steps {
                sh 'mvn clean compile'
            }
        }
        stage ('Scan SonarQube') {
            steps {
                withSonarQubeEnv(installationName:'SonarQube'){
                    sh 'mvn clean install sonar:sonar'
                }
            }
        }
        stage ('Test') {
            steps {
                sh 'mvn -Dmaven.test.failure.ignore=true clean install'
            }
        }
        stage('Deploy') {
            steps {
                echo "Deployment application à venir !!!"
            }
        }
    }
}
