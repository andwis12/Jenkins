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
                sh 'sfdx auth:jwt:grant --username $USERNAME \
                                            --jwtkeyfile $KEY_FILE \
                                            --clientid $CONSUMER_KEY \
                                            --setdefaultusername'
            }
        }

    }
}
