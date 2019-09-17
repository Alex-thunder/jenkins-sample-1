// Powered by Infostretch 

timestamps {

node () {

	stage ('App-IC - Checkout') {
 	 checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'admin', url: 'https://github.com/Alex-thunder/jenkins-sample-1.git']]]) 
	}
	stage ('App-IC - Build') {
 			// Maven build step
	withMaven(maven: 'maven') { 
 			if(isUnix()) {
 				sh "mvn clean package " 
			} else { 
 				bat "mvn clean package " 
			} 
 		}		// Shell build step
sh """ 
 
 """ 
	}
	stage('APP-IC - Quality Analysis'){
		withMaven(maven:'maven'){
			if(isUnix()){
				sh "mvn sonar:sonar"
			} else {
				bat "mvn sonar:sonar"
			}
		}
	}	
	stage ('App-IC - Post build actions') {
/*
Please note this is a direct conversion of post-build actions. 
It may not necessarily work/behave in the same way as post-build actions work.
A logic review is suggested.
*/
		// Mailer notification
		//step([$class: 'Mailer', notifyEveryUnstableBuild: false, recipients: 'jfmeng.alex@gmail.com', sendToIndividuals: false])
 
	}
}
}
