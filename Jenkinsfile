pipeline {
    agent any
    tools{
          maven "maven3.8.4"
    }

    triggers {
             // pollSCM('* * * * *')
    }

    parameters {
        string(name: 'project_name', defaultValue: 'Maven Pipeline', description: 'Jenkins Pipeline for Maven Project')
    }

    stages {

          stage('code checkout') {
               steps {
                      git branch: 'research', url: 'https://github.com/RaghavShetty78/maven-web-application.git'
                     }
          }

          stage('Build'){
		steps {
			sh "mvn clean package"
		}
	  }
    }
}
