@Library('jenkins-pipeline-shared-lib-sample') _

pipeline {
    agent any
    tools {
        maven 'mvn3'
    }

    stages {
        stage('Initialize') {
            steps {
                sh '''
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
                '''
            }
        }
        stage('Build') {
            steps {
                sh 'mvn -X clean install'
                echo 'Building..'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Starting int-test job') {
            steps {
                build job: 'integration-tests/drools-jenkins'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
                deploy()
            }
        }
    }
}

