pipeline {
	agent any
	stages{

	stage('code') {
  
      steps {
    git changelog: false, poll: false, url: 'https://github.com/Ajayaws773/mavenrepo.git'
      }
    }
    stage('build') {
  
      steps {
   sh 'mvn package'
      }
    }
stage('scan') {
  
      steps {
    withSonarQubeEnv(credentialsId: 'sonarid') {
    sh 'mvn sonar:sonar'
}
      }
    }
}

}
