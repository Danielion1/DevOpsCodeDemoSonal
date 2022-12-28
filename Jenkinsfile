pipeline {
    tools{
        maven 'myMaven'
    } 
    agent any 
    stages {
        stage('Clone Repo stage') { 
            steps {
                git 'https://github.com/Danielion1/DevOpsCodeDemoSonal.git'
            }
        }
        stage('Compile stage') { 
            steps {
                sh 'mvn compile'
                //windowm -bat 'mvn compile'
            }
        }
        stage('Code review stage ') { 
            steps {
                sh 'mvn pmd:pmd'
            }
        }
        stage('Unit Test stage') { 
            steps {
                sh 'mvn test'
            }
            post { 
                success {
                    junit 'target/surefire-reports/*.xml'
            }
        }
        }
        
        stage('Package Test stage') { 
            steps {
                sh 'mvn package'
            }
            post { 
                success {
                    jacoco()
            }
        }
        }
    }
}
