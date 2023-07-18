pipeline{

    agent any

    stages{
        stage('Checkout the code'){
            steps{
                git branch: 'main',  url: 'https://github.com/skmdab/create_sonarqube.git'
            }
        }

        stage('Creating server'){
            steps{
                sh "sh aws_create.sh"
            }
        }

        stage('Installing sonarqube package into server'){
            steps{
                withCredentials([file(credentialsId: 'pemfile', variable: 'PEMFILE')]) {
		   sh 'ansible-playbook installsonarqube.yaml --private-key="$PEMFILE"'
		}
            }
        }
    }
}
