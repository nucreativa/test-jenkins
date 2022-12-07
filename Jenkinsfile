pipeline {

    agent any

    environment {
        NEW_VERSION = '1.0.0'
        BRANCH_NAME = "${GIT_BRANCH.split("/").size() > 1 ? GIT_BRANCH.split("/")[1] : GIT_BRANCH}"
        REGISTRY = "YourDockerhubAccount/YourRepository"
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

            when {
                expression {
                    BRANCH_NAME == 'main'
                }
            }
            
            steps {
                echo 'pushing'
            }

        }

        stage("test") {

            steps {
                echo 'testing'
            }

        }

        stage("deploy") {

            steps {
                echo 'deploying'
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