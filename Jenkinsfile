pipeline{
    agent{
        label 'master'
    }
    tools{
        maven 'M3'   
    }
    stages{
        stage('Checkout'){
            steps{
                echo 'Checkout stage started'
                git branch: 'main', url: 'https://github.com/svnmp/SpringPetClinic.git'
                echo 'Checkout stage completed'
            }
        }
        stage('Build'){
           steps{
               echo 'Build stage started'
               sh 'mvn compile'
               echo 'Build stage completed'
           } 
        }
        stage('Test'){
            steps{
                sh 'mvn test'
            }
        }
        stage('Package'){
            steps{
                sh 'mvn -Dmaven.test.failure.ignore=true clean package'
            }
        }
        stage('Deploy'){
            steps{
                sh 'java -jar C:/Windows/System32/config/systemprofile/AppData/Local/Jenkins/.jenkins/workspace/PetClinicDeclarativePipeline/target/*.jar'
            }
        }
    }
}
