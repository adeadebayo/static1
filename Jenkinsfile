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
                 withAWS(region:'eu-west-2',credentials:'aws-static') {
                 sh 'echo "Uploading content with AWS credentials"'
                     s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file:'index.html', bucket:'jenkins-staticb')
           }
       }  
    }
}
}
