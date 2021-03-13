pipeline {
    agent any
    
    stages {
		stage('checkout') {
           steps {
             
                git branch: 'master', url: 'https://github.com/anisha-thakkar2020/hello-world-1.git'
             
          }
        }
        
		stage('Maven Build') {
            steps {
                ansiblePlaybook extras: '--connection=local -e ansible_python_interpreter=auto', installation: 'ansible', inventory: '/tmp/CI-JenkinsAnsible-SL/inventories/hosts', playbook: '/tmp/CI-JenkinsAnsible-SL/mavenBuild.yaml'			}
		}
		
		stage('Deploy and Restart tomcat') {
            steps {
                ansiblePlaybook installation: 'ansible', inventory: '/tmp/CI-JenkinsAnsible-SL/inventories/hosts', playbook: '/tmp/CI-JenkinsAnsible-SL/deployRestart.yaml'		
                
            }
	    }
}
}