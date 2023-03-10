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
  -Dsonar.host.url=http://3.140.254.136:9000 \\
  -Dsonar.login=40548287964066a8f31f2b60cc6bf8fefc9052ce'''
  }
  }
    stage("nexus"){
       steps{
       nexusArtifactUploader artifacts: [[artifactId: '$BUILD_TIMESTAMP', classifier: '', file: 'target/Calculator-1.0-SNAPSHOT.jar', type: 'JAR']], credentialsId: 'NEXUS_CREDENTIALS', groupId: 'fet1', nexusUrl: '52.14.253.253:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'test1', version: '$BUILD_ID'
       }
       }

}
}
