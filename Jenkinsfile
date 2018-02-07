#!/usr/bin/env groovy

// This file defines the Jenkins build pipeline for this project.


//=====================================================
// Constants and Parameters Definitions :: START
//=====================================================






//=====================================================
// Constants and Parameters Definitions :: END
//=====================================================



//=====================================================
// Jenkins Build Pipeline script :: START
//=====================================================

try {
    currentBuild.result = 'SUCCESS'

    node ('jenkins-mvn') {

    	//=============================================================================================
	    // Stage "Compile", "Static Analysis", "Tests" will:
	    //		1. Pull the latest code from BitBucket and compile the source code.
	    //		2. Execute static analysis with SonarQube.
	    //		3. Execute JUnit Tests.
	    //=============================================================================================

	    stage ('Compile') {
            checkout scm
            // NTUC sh "sudo chmod -R 755 build-env/* && dos2unix ./build-env/*.sh && ./build-env/jenkins-validate-archiva.sh && ./build-env/jenkins-compile.sh"
            // NTUC sh "sudo mkdir -p $ARTIFACT_LOCATION && sudo cp -R ./build-env $ARTIFACT_LOCATION && sudo cp -R ./cloud-formation $ARTIFACT_LOCATION  && sudo chown -R jenkins $ARTIFACT_LOCATION"
			//&& sudo cp -R ./app/src/main/resources/apps $ARTIFACT_LOCATION/apps 
            
            //added to tag git commit for upper environment deployment
            // NTUC gitCommit = sh(returnStdout: true, script: 'git rev-parse HEAD').trim()
			// NTUC shortCommit = gitCommit.take(6)
            
        }
		stage ('Static Analysis') {
            // NTUC sh "$ARTIFACT_LOCATION/build-env/jenkins-test-static-analysis.sh"
            //runSonarScan(env.SONAR_URL)
        }
        stage ('Tests') {
        	//Provision access for AWS IAM role with RT Cross Account credentials file.
            //sh "/build/obtain-cross-account-credentials.sh ${AWS_RT_IAM_CROSS_ACCOUNT}"
			// NTUC sh "/build/obtain-cross-account-credentials.sh ${AWS_RT_IAM_CROSS_ACCOUNT_CONFIG_DT}"

            //Unit Tests need access to AWS Elastic Search.
      	    // NTUC sh "$ARTIFACT_LOCATION/build-env/jenkins-test-unit-test.sh"
       	}
    }
}
catch (err) {
    currentBuild.result = 'FAILURE'
    throw err
}