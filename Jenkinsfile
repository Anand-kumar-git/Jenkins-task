pipeline {
    agent any

    stages {
        stage('Run Script') {
            steps {
                sh '''
                    chmod +x script.sh
                    ./script.sh > output.log 2>&1
                '''
            }
        }
    }

    post {
        always {
            emailext (
                subject: "Jenkins Build: ${env.JOB_NAME} #${env.BUILD_NUMBER} - ${currentBuild.currentResult}",
                body: """<p>Build Result: ${currentBuild.currentResult}</p>
                         <p>Check Jenkins for full console output: 
                         <a href="${env.BUILD_URL}console">${env.BUILD_URL}console</a></p>""",
                mimeType: 'text/html',
                to: 'anandkumard@gmail.com'
            )
        }
    }
}
