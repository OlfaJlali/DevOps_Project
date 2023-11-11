pipeline {

    agent any

    tools { nodejs '19.9.0'}

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
        stage('Jacoco Reports') {
             steps {
               echo "Publishing Jacoco Code Coverage Reports";
             }
             post {
                success {
                    jacoco(
                        execPattern: '**/target/*.exec',
                        )
                }

             }
        }
        stage('Deploy to Nexus') {
            steps {
                script {
                    // Maven deploy to Nexus
                    sh 'mvn deploy'
                }
            }
        }
        stage('build') {
            steps {
                sh 'mvn package'
            }
        }
         stage('Build Frontend') {
            agent any
                 steps {
                 // Checkout the Angular frontend repository
                 git branch: 'main',
                 url: 'https://github.com/HaithemGhattass/DevOpsFrontend.git'
                sh'rm -rf node_modules'
                sh'npm install'
                sh'npm cache clean --force'
                 sh 'npm install -g @angular/cli'
                 sh 'ng build --configuration=production'
                 }
         }
    }


}
