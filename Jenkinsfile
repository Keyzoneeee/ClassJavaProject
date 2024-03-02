pipeline {
    agent any
    
    options {
        skipDefaultCheckout() // Skip default checkout to perform custom Git configuration
    }
    
    parameters {
        string(name: 'CREDENTIALS_ID', defaultValue: 'your-credentials-id', description: 'Enter your Jenkins credentials ID')
    }
    
    tools {
        jdk 'myjava' 
        maven 'mymaven' 
    } 
     
    stages {
        stage('Clone Repo') { 
            steps { 
                withCredentials([usernamePassword(credentialsId: "${params.CREDENTIALS_ID}", usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                    git credentialsId: "${params.CREDENTIALS_ID}", 
                        url: 'https://github.com/Keyzoneeee/ClassJavaProject.git', 
                        username: Keyzoneeee, password: Samuel041012#
                }
            } 
        } 
         
        stage('Compile the code') { 
            steps { 
                sh 'mvn compile' 
            } 
        } 
         
        stage('Unit Testing') { 
            steps { 
                sh 'mvn test' 
            } 
        } 
         
        stage('Code Analysis') { 
            steps { 
                sh 'mvn pmd:pmd' 
            } 
        } 
         
        stage('Code coverage') { 
            steps { 
                sh 'mvn cobertura:cobertura -Dcobertura.report.format=xml' 
            } 
        } 
         
        stage('Build the artifact') { 
            steps { 
                sh 'mvn package' 
            } 
        } 
    } 
}
