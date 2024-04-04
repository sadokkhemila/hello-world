pipeline {
    agent any
    tools {
        maven "maven"
    }
    environment {
        NEXUS_VERSION = "nexus3"
        NEXUS_PROTOCOL = "http"
        NEXUS_URL = "51.38.50.55:8081"
        NEXUS_REPOSITORY = "testmaven"
        NEXUS_CREDENTIAL_ID = "nexus-cred"
        
    }
    stages {
        stage("Clone code from CVS") {
            steps {
                
                     git branch: 'main', url: 'https://github.com/sadokkhemila/hello-world.git'
                
            }
         }
         stage('Maven Package'){
		 steps {
	           sh 'mvn clean package'
		 }
        }
	stage('upload war to nexus'){
            script{
		def pomFile = readMavenPom file: 'pom.xml'
                nexusArtifactUploader artifacts: [

                    [
                        artifactId: 'maven-project',
                        classifier: '',
                        file: 'target/maven-project-1.0.0.war',
                        type: 'war'
                    ]
                ],
                credentialsId: NEXUS_CREDENTIAL_ID,
                groupId: 'com.example.maven-project', 
                nexusUrl: NEXUS_URL, 
                nexusVersion: NEXUS_VERSION, 
                protocol: NEXUS_PROTOCOL, 
                repository: 'http://51.38.50.55:8081/repository/testmaven/', 
                version: '1.0.0'
            }
        }
    }
}
    
