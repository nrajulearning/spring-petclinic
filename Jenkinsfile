node('build_java_11') {
    // get the git code from github
    stage ('code'){
        git branch: 'scripted', credentialsId: '04ea13ae-ce7c-4bc6-b5f0-c222ad85c12d', url: 'https://github.com/nrajulearning/spring-petclinic.git'
    }
    stage ('build_trigger'){
        properties([pipelineTriggers([pollSCM('0 * * * * ')])])
    }
    stage ('build'){
        sh 'mvn clean package'
    } 
    stage('Results') {
        junit '**/target/surefire-reports/TEST-*.xml'
        archiveArtifacts '**/target/*.war'
    }
}