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
        post{
                // If Maven was able to run the tests, even if some of the test
                // failed, record the test results and archive the jar file.
                success {
                    junit '**/target/surefire-reports/Test*.xml'
                    archiveArtifacts 'target/*.jar'
                }
            }
}