pipeline {
    agent {
        label 'build_java_11'
    }
    triggers{
        // Triggers pipeline for every 1hr
        cron '0 * * * *'
    }
   
    stages {
        stage('Build'){
        steps {
            // Run Maven on a Unix agent.
            sh "mvn clean package"

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