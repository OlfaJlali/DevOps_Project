pipeline {

    agent any
    stages {
        stage('Checkout Backend Repo') {
            steps {
              git branch: 'main',
              url: 'https://github.com/olfa213/DevOps_Project.git'
            }
        }
  stage('Unit Tests') {
            steps {
                script {
                    sh 'mvn test'
                }
            }
            post{
                        always{
                        junit '**/target/surefire-reports/TEST-*.xml'
                        }
                        }

        }
        stage('build') {
            steps {
                sh 'mvn package'
            }
        }



    }
 }
