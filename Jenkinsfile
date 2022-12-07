pipeline {

    agent any

    environment {
        NEW_VERSION = '1.0.0'
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
                    BRANCH_NAME == 'master'
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