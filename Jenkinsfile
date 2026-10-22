pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                git branch: 'main', url: 'https://github.com/KARTEEK0101/pet_shop.git'
            }
        }
        stage('Build'){
            steps{
                sh 'mvn clean package'
            }
        }
        stage('SonarQube Test'){
            steps{
                
         withSonarQubeEnv('SonarQube') {
             
             sh "mvn clean verify org.sonarsource.scanner.maven:sonar-maven-plugin:sonar -Dsonar.projectKey=petshop -Dsonar.projectName='Pet Shop'"
           
        }
            }
        }
        stage('Deploy to tomcat'){
            steps{
                deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: 'tomcatCred', path: '', url: 'http://13.201.190.182:8090/')], contextPath: 'app', war: '**/*.war'
            }
        }
       
    }
}
