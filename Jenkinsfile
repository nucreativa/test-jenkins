pipeline {

    agent any

    environment {
        REGISTRY = "nucreativa/test-jenkins"
        REGISTRY_CREDENTIALS = 'dockerhub'
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
                    docker.withRegistry( '', REGISTRY_CREDENTIALS ) {
                        dockerImage.push()
                    }
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