pipeline {
    agent any
    tools {
        maven "localmaven"
    }
    stages {
        stage('SCM Checkout'){
            steps{
                git credentialsId: 'git-cred', url: 'https://github.com/Swati1310/mavenproject.git'
            }
        }
        stage('MVN Build'){
            steps{
                sh "mvn -Dmaven.test.failure.ignore=true clean package"
            }
        }
        stage('MVN test'){
            steps{
                sh "mvn test"
            }
        }
        stage('test report'){
            steps{
                junit 'target/surefire-reports/*.xml'
            }
        }
        stage('archive'){
            steps{
                archiveArtifacts artifacts: 'target/*.jar', followSymlinks: false
            }
        }
    }
}
