node {
 stage('Code-checkout'){
   git 'https://github.com/RiteshDevOpsTrainer/may2020.git'
 }
 
 stage('Build'){
   def mvnHome = tool 'MVN_HOME'
   withEnv(["MAVEN_HOME=$mvnHome"]){
    sh '"$MAVEN_HOME/bin/mvn" clean install compile package'
   } 
 }
 
 stage('Deploy'){
  deploy adapters: [tomcat9(credentialsId: '751467ae-6526-4a63-a957-4797cb6c3351', path: '', url: 'http://192.168.1.103:9080')], contextPath: null, onFailure: false, war: '**/*war'
 }
 
 stage('Notification'){
  emailext attachLog: true, body: '''Dear Team, Your Job is build successfully. ''', subject: 'Jenkins Job Process', to: 'ritesh.goyal590@gmail.com'
 }

}
