pipeline {
    agent any
    options {
      skipDefaultCheckout true
    }
    tools {
      maven 'Maven_Home'
    }
    stages {
        stage ('------SCM START------') {
            steps {
               git branch: 'feature/APP-1', credentialsId: 'tapaswini-github-creds', url: 'https://github.com/tapaswsa/maven-app-project.git'
               echo "------- SCM STOP ------"
            }
        }
        stage ('Build') {
            steps {
               echo "Build start"
               sh "mvn clean install -DSkiptest"
               sh "ls -ltr target"
            }
        }
        stage ('Sonar Scan') {
            steps {
                echo "Sonar Scan"
                withSonarQubeEnv('Sonarqube Server') {
                    sh 'mvn sonar:sonar'
                }
                timeout(time: 2, unit: 'MINUTES') {
                    // Parameter indicates whether to set pipeline to UNSTABLE if Quality Gate fails
                    // true = set pipeline to UNSTABLE, false = don't
                    waitForQualityGate abortPipeline: true
                }
            }
        }
        stage ('Push Artifacts to Jfrog Artifactory') {
            steps {
                echo "Push Artifacts to Jfrog Artifactory" 
            }
        }
        stage ('Upload Docker Image to Jfrog Artifactory') {
            steps {
                echo "Upload Docker Image to Jfrog Artifactory" 
            }
        }
        stage ('Deployment') {
            steps {
                echo "Deployment" 
            }
        }
    }
}   
