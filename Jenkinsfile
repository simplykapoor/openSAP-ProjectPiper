@Library('piper-lib-os') _

node() {
  stage('init') {
    	deleteDir()
	checkout scm
	def folder = "openSAP-SampleFlow";
    	def filePath = folder + ".zip";
    	zip dir: folder, glob: '', zipFile: filePath;
  }
  stage('Upload, Deploy and Get MPL Status of Integration Artifact') {
  	setupCommonPipelineEnvironment script: this
	integrationArtifactUpload script: this
     	integrationArtifactDeploy script: this
	integrationArtifactGetMplStatus script: this
	print "MPL Status:" 
	print commonPipelineEnvironment.getValue("integrationFlowMplStatus")
  }
}
