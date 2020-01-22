@Library('CI_CD_PIPELINE@master') _
pipeline { agent { node { label 'linux1' } }
    stages {
  
    stage("upload")
     { 
     steps{
      script{
         def inputFile = input message: 'Upload file', parameters: [file(name: 'ssh.pem')]
         new hudson.FilePath(new File("$workspace/ssh.pem")).copyFrom(inputFile)
    
      }}
   } 

    stage('prepare ansible inventory'){
        steps {
    prepare_inventory(
    credentials_file: params.credentials_file
    )
    }
    }
       stage('Install java') {
            steps{
                sh """
                  ansible-playbook --private-key=./ssh.pem -i inventory javacheck.yml  --extra-vars "version=1.8.0_232" -vv
         """ 
            }}
    }
}

