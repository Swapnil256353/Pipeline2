node('master') {

stage ('checkout code'){
	checkout scm
}
	
stage ('Build'){
	sh "mvn clean install"
}

stage ('Test Cases Execution'){
	sh "mvn clean org.jacoco:jacoco-maven-plugin:prepare-agent install -Pcoverage-per-test"
}

stage ('Sonar Analysis'){
	//sh 'mvn sonar:sonar -Dsonar.host.url=http://localhost:80'
}

stage ('Archive Artifacts'){
	archiveArtifacts artifacts: '/var/lib/jenkins/.m2/repository/com/java/example/java-example/1.0-SNAPSHOT/*.war'
}
	
stage ('Deployment'){
	cd /var/lib/jenkins/.m2/repository/com/java/example/java-example/1.0-SNAPSHOT
	cp java-example-1.0-SNAPSHOT.war /opt/tomcat/webapps
}
}
