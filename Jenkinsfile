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
stage('SonarQube analysis') {
            steps {
                withSonarQubeEnv('sonar') {
                          sh 'mvn sonar:sonar'
                    }
                }
            }
stage('artifact') {
  
      steps {
   nexusArtifactUploader artifacts: [[artifactId: 'studentapp', classifier: '', file: 'target/studentapp-2.6-SNAPSHOT.war', type: 'war']], credentialsId: 'nexus', groupId: 'com.jdevs', nexusUrl: '43.204.229.189:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'maven-snapshots/', version: '2.6-SNAPSHOT'
      }
    }
stage('deployment') {
  
      steps {
  deploy adapters: [tomcat9(credentialsId: 'managertomcat', path: '', url: 'http://43.204.144.166:8080')], contextPath: null, war: '**/*.war'
      }
    }
}
}
