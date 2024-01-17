@Library('piper-lib-os') _
node() {
    stage('prepare') {
        checkout scm
        setupCommonPipelineEnvironment script:this
        piper version
    }	
    stage('abapLint') {
		dockerExecute(script: this, dockerImage: 'abaplint/abaplint:latest'){
		echo 'Running abaplint docker'
		sh 'npm i @abaplint/cli'
		sh 'abaplint'
		currentBuild.result = 'SUCCESS'		
		}
     }	
}