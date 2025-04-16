pipeline {  
    agent any

    stages{
        stage('zip the file'){
            steps{
                sh 'rm -rf *.zip || echo ""'
                sh 'zip -r ansible-${BUILD_ID}.zip * --exclude Jenkinsfile'
            }
        }
        stage('upload artifacts to jfrog'){
<<<<<<< HEAD
            steps
=======
            steps{
>>>>>>> 8a3dce0 (Jenkinsfile)
                sh 'curl -uadmin:AP53xfxUghB2m1yZ8yxc57jRpKJ -T \
                ansible-${BUILD_ID}.zip \
                "http://54.227.70.68:8081/artifactory/ansible/ansible-${BUILD_ID}.zip"'
            }
        }
        stage('publish to ansible server'){
            steps{
                sshPublisher(publishers: [sshPublisherDesc(configName: 'ansibleServer', \
                transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: \
                'unzip -o', execTimeout: 120000, flatten: false, makeEmptyDirs: false, \
                noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: \
                '/home/ec2-user', remoteDirectorySDF: false, removePrefix: '', \
                sourceFiles: 'ansible-${BUILD_ID}.zip')], usePromotionTimestamp: false, \
                useWorkspaceInPromotion: false, verbose: false)])
            }
        }
    }
}