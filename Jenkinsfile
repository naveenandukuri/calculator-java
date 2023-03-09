pipeline(){
agent any
   stages(){
      stage("git iinit"){
        steps{
	checkout scmGit(branches: [[name: '*/fet1']], extensions: [], userRemoteConfigs: [[url: 'git@github.com:naveenandukuri/calculator-java.git']])
	}
     }
}
}

