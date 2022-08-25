pipeline {
    agent any

    tools {
        maven 'Maven'
    }

    stages {
        stage('Build') {
            steps {
                sh 'mvn clean package'
                echo 'Building..'
            }
        }
        stage('Test') {
            steps {
                echo "Testing ${env.BUILD_NUMBER}"
            }
        }
        
        stage('Code Quality') {
            steps {
               echo 'Quality check'
               /* integrate with SonarQube */
            }

            post {
                failure {
                    echo 'Failure occurred'
                }
            }
        }
        
        stage('Deploy to Dev') {
            steps {
                echo 'Dev'
            }
        }

        stage('Deploy to Test') {
            steps {
                echo 'Test'
            }
        }

        stage('Deploy to UAT') {
            steps {
                echo 'UAT'
            }
        }

        stage('Deploy to Pre_prod') {
            steps {
                echo 'Staging'
            }
        }

        stage('Deploy to Prod') {
            steps {
                echo 'Production'
            }
        }
    }

    post {
        always {
            echo 'One way or another, I have finished'
            deleteDir() /* clean up our workspace */
        }
        success {
            echo 'I succeeded!'
        }
        unstable {
            echo 'I am unstable :/'
        }
        failure {
            mail to: 'team@example.com',
             subject: "Failed Pipeline: ${currentBuild.fullDisplayName}",
             body: "Something is wrong with ${env.BUILD_URL}"
        }
        changed {
            echo 'Things were different before...'
        }
    }
}