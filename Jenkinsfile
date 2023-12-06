pipeline {
    agent any
    options {
        // Timeout counter starts AFTER agent is allocated
        timeout(time: 1, unit: 'SECONDS')
    }
    stages {
        stage("Read DSV secrets") {
            steps {
                script {
                    // define a configuration that can be used for getting many secrets
                    def configuration = [tenant: 'https://labindsv.secretsvaultcloud.com', credentialsId: 'dsv_admin']
                    
                    def DSV_SECRET_VALUE = dsvSecret(config: configuration, secretPath: 'databases:us-west:db01', secretDataKey: 'username')
                    sh 'echo "$DSV_SECRET_VALUE"'
                    if (DSV_SECRET_VALUE == 'this is a secret') {
                        echo 'Ok'
                    } else {
                        echo 'Not ok'
                    }
                    
                    def SECRET1 = dsvSecret(config: configuration, secretPath: 'hello-world:jenkins', secretDataKey: 'secret1'){}
                    sh 'echo "$SECRET1"'
                    if (SECRET1 == 'value1') {
                        echo 'Ok'
                    } else {
                        echo 'Not ok'
                    }    
                }
            }
        }
    }
}