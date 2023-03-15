pipeline{
  agent {label 'JDK-JDK'}
  stages{
    stage('vcs'){
      steps{
        git url: 'https://github.com/chaitanyasagile/spring-petclinic.git',
            branch: 'develop'
      }
    }
    stage('build') {
      steps{
        sh './mvnw package'
      }
    }
    stage(sonar) {
      steps{
        withSonarQubeEnv('sonar_cloud') {
          sh 'mvnw clean package sonar:sonar -Dsonarlogin=7d97ec81447e87070bfedc6f0e450dc7c99b4bf2 -Dsonar.organization=suchi -Dsonar.projectKey=name'
        } 
      }
    }
  }
}