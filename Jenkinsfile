pipeline {
    agent any
    tools {
        maven "maven"
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
                  steps {
			nexusArtifactUploader artifacts: [
                          [
                             artifactId: 'maven-project',
                             classifier: '', 
                             file: 'target/Maven-Project-1.0.0.war',
                             type: 'war'
                          ]
                        ], 
                        credentialsId: 'nexus-cred', 
                        groupId: 'com.example.maven-project', 
                        nexusUrl: '51.38.50.55:8081', 
                        nexusVersion: 'nexus3', 
                        protocol: 'http', 
                        repository: 'http://51.38.50.55:8081/repository/testmaven/', 
                        version: '1.0.0'
		  }
            }
        } 
    }

    
