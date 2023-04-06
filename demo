pipeline{

    agent any

    environment {

        PATH = "$PATH:/opt/apache-maven-3.8.2/bin"

    }

    stages{

       stage('GetCode'){

            steps{

                git 'https://github.com/'

            }

         }       

       stage('Build'){

            steps{

                sh 'mvn clean package'

            }

         }

        stage('SonarQube analysis') {
steps{

        withSonarQubeEnv('sonarqube-8.9') {

        sh "${scannerHome}/bin/sonar-scanner"

        sh "mvn sonar:sonar"

    }

        }

        }
    }

}
