node{

buildName 'PROD - ${BUILD_NIMBER}'
buildDescription 'Pipeline Script - Scriptedway'


 
echo "The Node name is: ${env.NODE_NAME}"
echo "The Job name is: ${env.JOB_NAME}"
echo "The Build number is: ${env.BUILD_NUMBER}"

 properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '5')), pipelineTriggers([pollSCM('* * * * *')])])
 
def mavenHome = tool name: "maven-3.9.9"
 
//checkout stage   
stage('checkoutcode'){
    git credentialsId: 'Github_Credentials', url: 'https://github.com/Swaroop17y/maven-web-application.git'
}

//build stage
stage('build'){
    sh "$mavenHome/bin/mvn clean package"
}
 
/*
//generate SonarQube report
stage('SonarQube'){
    sh "$mavenHome/bin/mvn sonar:sonar"
}

//Upload Artifact into Artifcat Repository
stage('Artifact Nexus'){
    sh "$mavenHome/bin/mvn deploy"
}

//Deploy Application into Tomcat Server
stage('Tomcat Server'){
   sshagent(['04584455-d938-4cab-a869-7559b18d5d1e']) {
       sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@13.203.114.76:/opt/tomcat/webapps"
}
}
*/
}
