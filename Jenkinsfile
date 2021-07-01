pipeline{
    tools{
        jdk 'myjdk'
        maven 'mymaven'
    }
    agent none
    stages {

        stage('Compile'){
            agent any
            steps{
                sh 'mvn compile'
            }
        }
    
        stage('Test'){
            agent any
            steps{
                sh 'mvn test'
            }
            post{
                always{
                    junit 'gameoflife-web/target/surefire-reports/*.xml'
                }
            }
        }
        stage('Package'){
            agent {label 'win_salve'}
            steps{
                git 'https://github.com/Omid-Dahaghin/devops.git'
                bat 'mvn package'
            }
        }
    }
}
