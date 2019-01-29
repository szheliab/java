node {

def response

	stage('Checkout') {
		checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/tamamshud/java']]])     
	}

	stage('Maven build') {
		sh 'mvn clean package'
	}
	
	stage('Docker Build') {
	    sh 'sudo docker rm -f java_app && docker rmi my_app:my_app'
		sh 'sudo docker build -t my_app:my_app .'
	}

	stage('Docker RUN') {
		
		sh 'sudo docker run -d --name java_app -p 8383:8080  my_app:my_app'
	}   
	stage('Check Docker App') {
	    sh 'sleep 10'
	    sh 'curl http://10.28.13.24:8383/'
	}
	
	stage('CleanUp') {
		sh 'git clean -ffdx'
		deleteDir() 
	}
}
