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

stage('artifact') {
  
      steps {
   nexusArtifactUploader artifacts: [[artifactId: 'studentapp', classifier: '', file: 'target/studentapp-2.6-SNAPSHOT.war', type: 'war']], credentialsId: 'nexus', groupId: 'com.jdevs', nexusUrl: '3.7.254.3:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'maven-snapshots/', version: '2.6-SNAPSHOT'
      }
    }
stage('artifact') {
  
      steps {
  deploy adapters: [tomcat9(credentialsId: 'managertomcat', path: '', url: 'http://13.233.150.19:8080')], contextPath: null, war: '**/*.war'
      }
    }
}
}
