pipeline {
  agent any
  stages {
    stage('Code Checkout ') {
      steps {
        git(url: 'ssh://hkalthir-in@rchgit01.rchland.ibm.com:29418/pse-test/fsp-ct', branch: '*/master')
      }
    }

    stage('Execute') {
      steps {
        sh '''cd $WORKSPACE/$BUILD_NUMBER/fsp-ct
python2.7 tools/hmc_infra_tools/InfraTool.py -F ProvisionAixPartition -M $Managed_System -P $LPAR_Name -H $HMC_IP -A $HMC_Password -B $Build
'''
      }
    }

  }
}