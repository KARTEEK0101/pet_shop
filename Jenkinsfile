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
        stage('Deploy to tomcat'){
            steps{
                deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: 'sandeepcred', path: '', url: 'http://13.203.213.139:8090/')], contextPath: 'app', war: '**/*.war'
            }
        }
       
    }
}
