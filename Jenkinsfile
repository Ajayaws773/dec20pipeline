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
stage(SonarQube analysis') {
            steps {
                withSonarQubeEnv('sonarid') {
                        withMaven(maven:'Maven 3.5') {
                        sh 'mvn sonar:sonar'
                    }
                }
            }
        }
}

}
