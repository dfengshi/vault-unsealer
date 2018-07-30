
#!Groovy
@Library("platform.infrastructure.pipelinelibrary") _

// Global Pipeline Settings, like keep the 10 most recent builds, etc
withGlobalPipelineProperties () {

	// Begin Build/CI Section
	def buildNodeId = platformDefaults.getBuildNodeLabel()

	// Node properties to setup logs to send to aggr(sumo)
	withNodeWrapper(buildNodeId) {

        // Ensure we start with an empty directory.
        deleteDir()

        //Checkout SCM
        stage("Checkout SCM") { 
            checkout scm           
        }

        //Build Push Container
        stage('Build Image') {
                dockerBuildPush()
        }
    }
}
