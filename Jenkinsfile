pipeline {
    agent {
        label 'sfdx'   
    }
    
    environment{
           KEY_FILE = credentials('SERVERKEY')
           CONSUMER_KEY = credentials('CONSUMER_KEY')
           USERNAME = credentials('USERNAME')
    }

    stages {

        stage('Hello') {
            steps {
                script{
                    withCredentials([
                        string(credentialsId: "${USERNAME}", variable: "AUTH_USERNAME"),
                        file(credentialsId: "${SERVER_KEY}", variable: "AUTH_SERVER_KEY"),
                        string(credentialsId: "${CONSUMER_KEY}", variable: "AUTH_CONSUMER_KEY")
                    ]){
                        echo "---- Authenticate to ${TARGET_ORG} ----"
                          sh 'sfdx auth:jwt:grant --username $USERNAME \
                                            --jwtkeyfile $KEY_FILE \
                                            --clientid $CONSUMER_KEY \
                                            --setdefaultusername'
                    }
                }
              
            }
        }

    }
}
