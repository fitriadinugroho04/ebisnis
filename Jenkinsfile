pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/username/my-app.git'
            }
        }

        stage('Build') {
            steps {
                echo 'Building aplikasi...'
            }
        }

        stage('Test') {
            steps {
                echo 'Menjalankan test...'
            }
        }

        stage('Deploy') {
            steps {
                sshPublisher(
                    publishers: [
                        sshPublisherDesc(
                            configName: 'server-prod',
                            transfers: [
                                sshTransfer(
                                    sourceFiles: '**/*',
                                    remoteDirectory: '/var/www/html/myapp',
                                    cleanRemote: false
                                )
                            ]
                        )
                    ]
                )
            }
        }
    }
}
