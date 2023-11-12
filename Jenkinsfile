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
        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv(installationName:'sql') {
                    sh 'chmod +x ./mvnw'
                    sh 'mvn package sonar:sonar'
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
        stage('Build docker image'){
            steps{
                script{
                    sh 'docker build -t olfajlali/spring-boot-docker .'
                }
            }
        }
        stage('Push beckend image to Hub'){
            steps{
                script{
                    withCredentials([string(credentialsId: 'dockerhub-pwd', variable: 'dockermdp')]) {
                    sh 'docker login -u olfajlali -p ${dockermdp}'
                    }
                    sh 'docker push olfajlali/spring-boot-docker'
                }
            }
        }
        stage('Build Frontend') {
            agent any
            steps {
                // Checkout the Angular frontend repository
                git branch: 'main',
                url: 'https://github.com/olfa213/DevOps_Project_Front.git'
                sh 'rm -rf node_modules'
                sh 'npm install'
                sh 'npm install -g @angular/cli'
                sh 'ng build --configuration=production'
                sh 'docker build -t olfajlali/angular-app -f Dockerfile .'
                withCredentials([string(credentialsId: 'dockerhub-pwd', variable: 'dockermdp')]) {
                sh 'docker login -u olfajlali -p ${dockermdp}'
                sh 'docker push olfajlali/angular-app'
                }
            }
        }
        stage('docker-compose full stack app'){
            steps{
                script{
                    sh 'docker compose up --build -d'
                }
            }
        }
    }


}