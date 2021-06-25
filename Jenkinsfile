#!/usr/bin/env groovy
import hudson.model.*
import hudson.EnvVars
import groovy.json.JsonSlurper
import groovy.json.JsonBuilder
import groovy.json.JsonOutput
import java.net.URL


 String Git_Credentials      = "GitHub_ralphnuesse"
 String Git_URL              = "https://github.com/CPWRGIT/ISPWSA0_CWC2.git"
 String ISPW_Application     = "GITA"
 String HCI_Conn_ID          = "38e854b0-f7d3-4a8f-bf31-2d8bfac3dbd4"
 String HCI_Token            = "HDDRXM0"               //cwcc
 String ISPW_Stream          = "GITDEMO1"
 String CES_TOKEN            = "6839356e-0256-4a8f-8de9-3d223a1b7d36"        //6839356e-0256-4a8f-8de9-3d223a1b7d36 
 String LEVEL
 String ASSIGNMENT


/* 
  Node is a required part of the Jenkins pipeline for any steps to be executed
*/ 
node{

    /*  This stage will retrieve the code from Git   */
    stage("Checkout")
    {
      checkout scm
    }    
    
    /*  This loads the changed files into ISPW    */ 
    stage("Loading Mainframe code to ISPW") 
    {
            gitToIspwIntegration app: "${ISPW_Application}", 
            branchMapping: '''*main* => MAIN, per-branch
            feature* => FT1, per-commit
            bug* => HFIX, per-commit''', 
            connectionId: "${HCI_Conn_ID}", 
            credentialsId: "${HCI_Token}", 
            gitCredentialsId: "${Git_Credentials}", 
            gitRepoUrl: "${Git_URL}", 
            runtimeConfig: 'ISPW', 
            stream: "${ISPW_Stream}"
 
    }
}
