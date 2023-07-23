node
{
    properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '', daysToKeepStr: '', numToKeepStr: '5')), pipelineTriggers([pollSCM('* * * * *')])])
    echo "Buld number is {$env.BUILD_NUMBER}"
    echo "Job number is {$env.JOB_NAME}"
    def mavenhome = tool name: "maven 3.9.3"
    stage("Code pull"){
        git credentialsId: '28c6da8a-6bfa-4843-9a6a-567141de2e91', url: 'https://github.com/DevopsLokey/maven-web-application.git'
    }
    
    stage("Code build"){
        sh "${mavenhome}/bin/mvn clean package"
    }
    /*
     stage("Code test"){
        sh "${mavenhome}/bin/mvn clean sonar:sonar"
    }
    stage("Code into artofacts"){
        sh "${mavenhome}/bin/mvn clean deploy"
    }
    
    stage("Deploy to tomcat"){
        sshagent(credentials: ['57d0d866-cd7a-47c2-a922-4cfb6ad11056']) {
    sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war lokesh@192.168.100.42:/opt/tomcat/webapps/"
}
    }
    */
}
