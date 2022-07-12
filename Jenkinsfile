pipeline {
    agent any
    tools{
          maven "maven3.8.4"
    }
    /*
    triggers {
             // pollSCM('* * * * *')
    }
    */
    parameters {
        string(name: 'project_name', defaultValue: 'Maven Pipeline', description: 'Jenkins Pipeline for Maven Project')
    }

    stages {

          stage('code checkout') {
               steps {
                      git branch: 'research', url: 'https://github.com/RaghavShetty78/maven-web-application.git'
                     }
          }

          stage('Build') {
		steps {
			sh "mvn clean package"
		}
	  }
          stage('Approval') {
            // no agent, so executors are not used up when waiting for approvals
            agent none
            steps {
                script {
                    def deploymentDelay = input id: 'Deploy', message: 'Want to continue ${params.project_name}?', submitter: 'raghav,admin', parameters: [choice(choices: ['0', '1', '2', '3', '4', '5', '6', '7', '8', '9', '10', '11', '12', '13', '14', '15', '16', '17', '18', '19', '20', '21', '22', '23', '24'], description: 'Seconds to delay deployment?', name: 'deploymentDelay')]
                    sleep time: deploymentDelay.toInteger(), unit: 'SECONDS'
                }
            }
          }


    }
}
