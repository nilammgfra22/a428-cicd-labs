node {
    docker.image('node:16-buster-slim').withRun('-p 3000:3000') {
        stage('Build') {
            steps {
                sh 'npm install'
            }
        }

        stage('Test') {
            steps {
                sh './jenkins/scripts/test.sh'
            }
        }

        stage('Deploy') {
            steps {
                sh './jenkins/scripts/deliver.sh'
                input message: 'Lanjutkan ke tahap Deploy? klik Proceed (lanjut) atau Abort (menghentikan eksekusi pipeline)'
                sh './jenkins/scripts/kill.sh'
            }
        }
    }
}