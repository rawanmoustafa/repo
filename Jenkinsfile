pipeline {
  agent any
  stages {

    stage('Lint HTML') {
      steps {
        sh 'tidy -q -e *.html'
      }
    }
    
    stage('Upload to AWS') {
      steps {
        withAWS(region: 'us-west-2', credentials: '	0c87a023-f707-4828-838c-7293710b813f') {
          sh 'echo "Uploading content with AWS creds"'
          s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file: 'index.html', bucket: 'rawan-bucket-95')
        }

      }
    }

  }
}
