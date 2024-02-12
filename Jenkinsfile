podTemplate(containers: [
  containerTemplate(
      name: 'maven',
		image: 'adoptopenjdk/maven-openjdk8', 
		command: 'sleep',
		args: '30d'
      )
  ], 
  
  volumes: [
  persistentVolumeClaim(
      mountPath: '/root/.m2/repository', 
      claimName: 'jenkins-pv-claim', 
      readOnly: false
      )
  ]) 

{
  node(POD_LABEL) {
    stage('Get a Maven project') {
      git 'https://github.com/bingbingkuai/simple-java-maven-app.git'
      container('maven') {
        sh 'mvn -B -ntp clean package -DskipTests'
      }
    }
  }
}
