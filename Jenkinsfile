node('build_java_11') {
    // get the git code from github
    stage ('code'){
        git 'https://github.com/nrajulearning/spring-petclinic.git'
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