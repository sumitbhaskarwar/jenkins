node {
 stage('Code-checkout'){
   git 'https://github.com/sumitbhaskarwar/Test_Sumit_Devops.git'
 }
 
 stage('Build'){
   def mvnHome = tool 'Maven'
   withEnv(["Maven=$mvnHome"]){
    sh '"$Maven/bin/mvn" clean install compile package'
   } 
 }
 
 stage('Deploy'){
  deploy adapters: [tomcat9(credentialsId: 'e62016f9-2498-469a-af1a-390014fea702', path: '', url: 'http://192.168.1.102:9080')], contextPath: null, onFailure: false, war: '**/*war'
 }
 
 stage('Notification'){
  emailext attachLog: true, body: '''Dear Team, Your Job is build successfully. ''', subject: 'Jenkins Job Process', to: 'sumitbhaskarwar@yahoo.com'
 }

}
