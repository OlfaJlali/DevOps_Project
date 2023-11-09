pipeline {

    agent any
    stages {
        stage('Checkout Backend Repo') {
            steps {
              git branch: 'main',
              url: 'https://github.com/olfa213/DevOps_Project.git'
            }
        }

        stage('build') {
            steps {
                sh 'mvn package'
            }
        }



    }
 }
