node {
    stage('Build') {
        // Install required plugins
        checkout scm
        stage('Install Dependencies') {
            withNodeJS {
                sh 'npm install'
            }
        }
    }
    stage('Test') {
        withNodeJS {
            sh './jenkins/scripts/test.sh'
        }
    }
    stage('Deploy') {
        withNodeJS {
            sh './jenkins/scripts/deliver.sh'
            input message: 'Sudah selesai menggunakan React App? (Klik "Proceed" untuk mengakhiri)'
            sh './jenkins/scripts/kill.sh'
        }
    }
}