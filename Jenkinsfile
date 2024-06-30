pipeline {
  agent any
    parameters {  choice(name: 'Branch_Name', choices: ['jar', 'war', 'master'], description: '') }
	stages {
	  stage('scm'){
	    steps {	
		git branch: '${Branch_Name}', url: 'https://github.com/awskaizen02/j11.git'
		  }
			}
	stage('Build'){
	  steps {
		sh 'mvn clean'
		sh 'mvn install'

		}
			}
	stage('Deploy'){
	  steps {
		deploy adapters: [tomcat9(credentialsId: 'web', path: '', url: 'http://65.2.10.90:8888/')], contextPath: 'un-pipeline', war: '**/*.war'
		}
			}	
	}

}
