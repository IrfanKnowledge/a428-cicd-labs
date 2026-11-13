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
    }
}
