pipeline {
    agent any
    stages {
        stage('Lint all HTML files') {
              steps {
                  sh 'tidy -q -e *.html'
              }
         }
        stage('Upload to AWS') {
            steps {
                withAWS(region:'us-west-2',credentials:'aws-devops') {
                sh 'echo "Uploading content with AWS creds"'
                    s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file:'index.html', bucket:'s3-devops-course3')
                }
            }
        }
    }
}
