node {
    docker.image('node:16-buster-slim').inside('-p 3000:3000') {
        stage('Build') {
            sh 'npm install'
        }
        stage('Test') { 
            sh './jenkins/scripts/test.sh' 
        }
        stage('Manual Approval') {
            input message: 'Lanjutkan ke tahap Deploy? (Click "Proceed" or "Abort")'
        }
        stage('Deploy') {
            sh './jenkins/scripts/deliver.sh'
            sh './jenkins/scripts/kill.sh'
            sleep(time: 1, unit: "MINUTES")
            echo "Eksekusi pipeline sukses"
        }
    }
}