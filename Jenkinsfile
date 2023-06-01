pipeline {
    agent {
        docker {
            image 'node:16-buster-slim'
            args '-p 3000:3000'
        }
    }
    stages {
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
                sleep(time: 60, unit: 'SECONDS') // Menjeda selama 1 menit
            }
        }
    }
}