pipeline(){
agent any
   stages(){
      stage("git iinit"){
        steps{
          git branch: 'fet1', url: 'https://github.com/naveenandukuri/calculator-java.git'
     }
}
      stage("maven build"){
         steps{
	 sh 'mvn clean package'
	 }
     }
     stage("sonarqube"){
        steps{
	sh '''mvn sonar:sonar \\
  -Dsonar.projectKey=calculatorfet1 \\
  -Dsonar.host.url=http://18.116.53.46:9000 \\
  -Dsonar.login=40548287964066a8f31f2b60cc6bf8fefc9052ce'''
  }
  }
    stage("nexus"){
       steps{
       nexusArtifactUploader artifacts: [[artifactId: '$BUILD_TIMESTAMP', classifier: '', file: 'target/Calculator-1.0-SNAPSHOT.jar', type: 'JAR']], credentialsId: 'NEXUS_CREDENTIALS', groupId: 'fet1', nexusUrl: '18.118.106.173:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'test1', version: '$BUILD_ID'
       }
       }
       stage("tomcat"){
       steps{
       deploy adapters: [tomcat9(credentialsId: 'TOMCAT_CRED', path: '', url: 'http://3.15.222.175:8080/')], contextPath: '/manager/text/deploy?path=/qaenv', onFailure: false, war: 'jar'
       }
       }

}
}
