pipeline{
    agent any
    stages{
        stage('checkout'){
            steps{
                checkout scm
            }
        }
        stage('build'){
            steps{
                sh "docker build -t sample-react-app ."
            }
        }
    }

}