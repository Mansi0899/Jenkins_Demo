pipeline {
    agent any
    tools {
        maven 'maven-3.8.6' 
    }
    environment {
        DATE = new Date().format('yy.M')
        TAG = "${DATE}.${BUILD_NUMBER}"
    }
    stages {
        stage ('Build') {
            steps {
                sh 'mvn -B -DskipTests clean package'
            }
        }
        
        stage('Test'){
            steps {
                sh 'mvn test'
            }
        } 
        stage('Deliver') { 
            steps {
                sh './jenkins/scripts/deliver.sh' 
           }
        }
 }
}
