pipeline {
    agent any
    stages {
        stage ('SCM') {
            steps {
               echo "SCM"
            }
        }
        stage ('Build') {
            steps {
               echo "Build"
            }
        }
        stage ('Sonar Scan') {
            steps {
                echo "Sonar Scan" 
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
