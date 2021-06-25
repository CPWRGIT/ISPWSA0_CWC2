#!/usr/bin/env groovy
import hudson.model.*
import hudson.EnvVars
import groovy.json.JsonSlurper
import groovy.json.JsonBuilder
import groovy.json.JsonOutput
import java.net.URL


 String Git_Credentials      = "githubenterprise-pfhsxk0"
 String Git_URL              = "http://dtw-githubenterprise.nasa.cpwr.corp/pfhsxk0/GIT1.git"
 String ISPW_Application     = "GITA"
 String HCI_Conn_ID          = "38e854b0-f7d3-4a8f-bf31-2d8bfac3dbd4"
 String HCI_Token            = "cwc2"               //cwcc
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
            branchMapping: '''*master* => MSTR, per-branch
            feature1 => FT1, per-branch
            Bug => HFIX, per-branch''', 
            connectionId: "${HCI_Conn_ID}", 
            credentialsId: "${HCI_Token}", 
            gitCredentialsId: "${Git_Credentials}", 
            gitRepoUrl: "${Git_URL}", 
            runtimeConfig: '', 
            stream: "${ISPW_Stream}"
 
    }
}
