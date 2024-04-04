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
    }
}
    
