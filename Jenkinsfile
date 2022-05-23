pipeline {
    agent {
        label 'build_java_11'
    }
    triggers{
        // Triggers pipeline for every 1hr
        POLLSCM '0 * * * *'
    }
   
    stages {
        stage('Build the code and sonarqube-analysis'){
        steps {
            withSonarQubeEnv('sonar-9.4.0') {
                 sh 'mvn clean package sonar:sonar'
              }

            }
        }

        stage('Results'){
        steps {
                junit '**/target/surefire-reports/TEST-*.xml'
                archiveArtifacts '**/target/*.jar'          
            }
        }
    }
        post {
        success {
            echo 'Build creation is successfully'
            }
        }
}