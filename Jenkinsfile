pipeline {
    agent any
    tools {
        maven "maven"
    }
    stages {
        stage("Clone code from CVS") {
            steps {
                
                     git branch: 'main', url: 'https://github.com/sadokkhemila/mecen.ai.git'
                
            }
         }
         stage('Maven Package'){
	           sh 'mvn clean package'
	           
        }
    }
}
    
