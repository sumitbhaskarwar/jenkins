node {
	
	stage('Preparation'){
	  git 'https://github.com/RiteshDevOpsTrainer/may2020.git'
	}
	
	stage('Build'){
	  def mvnHome = tool 'M2_HOME'
	  withEnv(["MVN_HOME=$mvnHome"]){
	    sh '"$MVN_HOME/bin/mvn" clean install compile package'
	  }
	}
	
	stage('Deploy'){
	  git 'git://github.com/RiteshDevOpsTrainer/ansible.git'
      sh 'echo "Deploying Hot backup"'
      sh 'sudo ansible-playbook -i hosts deploy.yml' 
	}
	
	stage('Notification'){
	 emailext attachLog: true, body: '''Hi User, please find your project status''', subject: 'Jenkins Pipeline Build ', to: 'ritesh.goyal590@gmail.com'
	}
	
	stage('Print'){
	 sh 'echo "The DevOps Pipeline project is successfull"'
	}
}  
