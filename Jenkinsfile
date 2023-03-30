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

                    withCredentials([
                        string(credentialsId: 'USERNAME'}, variable: "AUTH_USERNAME"),
                        file(credentialsId: 'SERVERKEY', variable: "AUTH_SERVER_KEY"),
                        string(credentialsId: 'CONSUMER_KEY', variable: "AUTH_CONSUMER_KEY")
                    ]){
                          sh 'sfdx auth:jwt:grant --username $AUTH_USERNAME \
                                            --jwtkeyfile $AUTH_SERVER_KEY \
                                            --clientid $AUTH_CONSUMER_KEY \
                                            --setdefaultusername'
                    }
                
              
            }
        }

    }
}
