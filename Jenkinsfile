pipeline {
agent any
tools {
	maven 'MAVEN_HOME'
        jdk 'JAVA_HOME'
}
stages {
stage ('Build') {
	steps {
		echo "Building Project"
		bat '''
			mvn clean install
		'''
	}
}
stage('Test') {
        steps {
             bat '''
             	  	mvn -B verify
             '''
        }
}
stage('Deploy') {
	steps {
		echo "Deploying"
		deploy adapters: [tomcat9(credentialsId: '055f2355-243e-4ffe-8b3b-8c90beab6f98', path: '', url: 'http://localhost:8080')], contextPath: 'FinalShopizer', war: '**/*.war'
	    }
    }
}
}
