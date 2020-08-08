node {
	
	stage('Preparation'){
	  git 'https://github.com/sumitbhaskarwar/Test_Sumit_Devops.git'
	}
	
	stage('Build'){
	  def mvnHome = tool 'Maven'
	  withEnv(["MAVEN_HOME=$mvnHome"]){
	    sh '"$MAVEN_HOME/bin/mvn" clean install compile package'
	  }
	}
	
	stage('Deploy'){
	  git 'https://github.com/sumitbhaskarwar/ansible.git'
      sh 'echo "Deploying Hot backup"'
      sh 'sudo ansible-playbook -i hosts deploy.yml' 
	}
	
	stage('Notification'){
	 emailext attachLog: true, body: '''Hi User, please find your project status''', subject: 'Jenkins Pipeline Build ', to: 'sumitbhaskarwar@gmail.com'
	}
	
	stage('Print'){
	 sh 'echo "The DevOps Pipeline project is successfull"'
	}
}  
