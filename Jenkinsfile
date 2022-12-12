pipeline {

    agent any

    environment {
        REGISTRY = "nucreativa/test-jenkins"
    }

    stages {

        stage('clone repository') {
           
            steps {
                echo 'cloning'
                checkout scm
            }

        }

        stage("build") {
            
            steps {
                echo 'building'
                script {
                    dockerImage = docker.build REGISTRY + ":$BUILD_NUMBER"
                }
            }

        }

        stage("push") {
            
            steps {
                echo 'pushing'
                script {
                    dockerImage.push()
                }
            }

        }

        stage('Cleaning up') {
            steps{
                sh "docker rmi $REGISTRY:$BUILD_NUMBER"
            }
        }

    }

    // post {
    //     always {

    //     }
    //     success {

    //     }
    //     failure {

    //     }
    // }
}