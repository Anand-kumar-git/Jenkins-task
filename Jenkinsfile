pipeline {
    agent any

    stages {
        stage('Run Script') {
            steps {
                sh '''
                    chmod +x script.sh
                    ./script.sh
                '''
            }
        }
    }

    post {
        always {
            script {
                def log = currentBuild.rawBuild.getLog(1000).join('\n')
                emailext (
                    subject: "Jenkins Build Log: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                    body: """
                        <h2>Build Result: ${currentBuild.currentResult}</h2>
                        <p>Build Number: ${env.BUILD_NUMBER}</p>
                        <pre>${log}</pre>
                    """,
                    mimeType: 'text/html',
                    to: 'anandkumard1553@gmail.com'
                )
            }
        }
    }
}
