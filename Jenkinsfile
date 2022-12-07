pipeline {

    agent any

    environment {
        NEW_VERSION = '1.0.0'
        BRANCH_NAME = "${GIT_BRANCH.split("/").size() > 1 ? GIT_BRANCH.split("/")[1] : GIT_BRANCH}"
    }

    stages {

        stage("build") {
            
            steps {
                echo 'building'
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