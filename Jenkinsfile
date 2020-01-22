@Library('CI_CD_PIPELINE@master') _
pipeline { agent { node { label 'linux1' } }
    stages {
    stage("Interactive_Input") {
            steps {
                script {

                    // Variables for input
                    def inputConfig
                    def userInput = input(
                          id: 'userInput', message: 'enter the java version :?',
                            parameters: [

                                    string(defaultValue: 'None',
                                            description: 'java version',
                                            name: 'jversion')
                             ])
                    java_version=userInput.jversion:
          }
       }
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
                  ansible-playbook  -i inventory javacheck.yml  --extra-vars "version=$java_version" -vv
         """ 
            }}
    }
}

