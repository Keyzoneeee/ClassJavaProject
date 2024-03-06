pipeline {
    agent any
    
    stages {
        stage('Clone Repo') {
            steps {
                git 'https://github.com/Keyzoneeee/ClassJavaProject.git'
            }
        }
        
        stage('Compile the code') {
            steps {
                sh 'mvn compile'
            }
        }
        
        stage('Unit Testing') {
            steps {
                script {
                    // Assigning the path to a variable
                    def surefireReportsPath = 'Surefire reports path: target/surefire-reports/*.xml'
                    // Now you can use 'surefireReportsPath' as needed without printing it
                }
            }
            post {
                success {
                    echo 'Post success action'
                    // Additional actions to take upon successful completion of the stage
                }
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
        
        stage('Package on master') {
            steps {
                sh 'mvn package'
            }
        }
    }
}
