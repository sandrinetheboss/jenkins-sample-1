// Powered by Infostretch 

timestamps {

node () {

	stage ('App-IC - Checkout') {
 	 checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'git-login', url: 'https://github.com/sandrinetheboss/jenkins-sample-1.git']]]) 
	}
	stage ('App-IC - Build') {
 	
// Unable to convert a build step referring to "hudson.plugins.sonar.SonarBuildWrapper". Please verify and convert manually if required.		// Maven build step
	withMaven(maven: 'maven-3') { 
 			if(isUnix()) {
 				sh "mvn clean package " 
			} else { 
 				bat "mvn clean package " 
			} 
 		}		// Maven build step
	withMaven(maven: 'maven-3') { 
 			if(isUnix()) {
 				sh "mvn sonar:sonar " 
			} else { 
 				bat "mvn sonar:sonar " 
			} 
 		}
		// JUnit Results
		junit '**/target/surefire-reports/*.xml' 
	}
}
}
