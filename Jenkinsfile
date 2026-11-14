node {
    withEnv(['CI=true', 'NODE_OPTIONS=--openssl-legacy-provider']) {
        stage('Build') {
            checkout scm
            sh 'npm install'
        }
        stage('Test') {
            sh 'chmod +x ./jenkins/scripts/test.sh'
            sh './jenkins/scripts/test.sh'
        }
        stage('Manual Approval') {
            input message: 'Lanjutkan ke tahap Deploy?'
        }
        stage('Deploy') {
            sh 'chmod +x ./jenkins/scripts/deliver.sh ./jenkins/scripts/kill.sh'
            sh './jenkins/scripts/deliver.sh'
            sleep 60
            sh './jenkins/scripts/kill.sh'
        }
    }
}
