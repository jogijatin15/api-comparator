pipeline {
    agent any
    stages {
        stage('API Comparison') {
            steps {
							slackSend color: "229954",message: "Starting *API Comparator* Job"
							slackSend color: "cceef9", message: "`Initializing APIs..` Job Details: ${env.JOB_NAME} ${env.BUILD_NUMBER} (<${env.BUILD_URL}|Open>)"

               sh '''
                ls /tmp
                curl -c /tmp/api.cookie ${API_COMPARATOR}/login -H 'Content-Type: application/x-www-form-urlencoded' --data 'username=admin&password=admin&submit=Login' -v
                curl -b /tmp/api.cookie ${API_COMPARATOR}/runproject/APIComp?apic=true -v
                '''

								slackSend color: "cceef9", message: "`API Comparison Completed` View Results Here: Details: (<${env.API_COMPARATOR}|Reports>)"

            }
        }
    }
}
