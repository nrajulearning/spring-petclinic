pipeline {
    agent {
        label 'build_java_11'
    }
    triggers{
        // Triggers pipeline for every 1hr
        pollSCM '0 * * * *'
    }
   
    stages {
        stage('Build'){
        steps {
            // Run Maven on a Unix agent.
            sh "mvn clean package"

            }
        }
        
    }
}