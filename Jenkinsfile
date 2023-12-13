pipeline {
    agent any
    stages {
        stage("Read DSV secrets") {
            steps {
                script {
                    // define a configuration that can be used for getting many secrets
                    def configuration = [tenant: 'labindsv', credentialsId: 'dsv_admin']
                    
                    def DSV_SECRET_VALUE = dsvSecret(config: configuration, secretPath: 'databases:us-west:db01', secretDataKey: 'username')
                    sh 'echo "$DSV_SECRET_VALUE"'
                    
                    def SECRET1 = dsvSecret(config: configuration, secretPath: 'databases:us-west:db01', secretDataKey: 'password'){}  
                }
            }
        }
    }
}