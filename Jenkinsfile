pipeline{
    agent any

    stages{
        stage('zip the file'){
            steps{
                sh 'rm -rf *.zip || echo ""'
                sh 'zip -r ansible-${BUILD_ID}.zip * --exclude Jenkinsfile'
            }
        }
        stage('upload artifacts to jfrog'){
            steps{
                sh 'curl -uadmin:AP53xfxUghB2m1yZ8yxc57jRpKJ -T \
                ansible-${BUILD_ID}.zip \
                "http://34.202.229.63:8081/artifactory/ansible/ansible-${BUILD_ID}.zip"'
            }
        }
    }    
}    