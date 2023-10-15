pipeline{
    agent {label 'slave2'}
    stages{
       stage('Git Checkout Stage'){
            steps{
                git branch: 'main', url: 'https://github.com/rohith-marigowda/sonarqube-example.git'
            }
         }        
       stage('Build Stage'){
            steps{
                sh 'mvn clean install'
            }
         }
        stage('SonarQube Analysis Stage') {
            steps{
                withSonarQubeEnv('sonarqube') { 
                    sh "mvn clean verify sonar:sonar -Dsonar.projectKey=sonar-test"
                }
            }
        }
    }
}
