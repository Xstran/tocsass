pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/Xstran/tocsass.git', branch: 'main'
            }
        }
        stage('Build') {
            steps {
                echo 'Building..'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying..'
                sshPublisher(
                    publishers: [
                        sshPublisherDesc(
                            configName: 'myUserver',
                            transfers: [sshTransfer(sourceFiles: '*/', remoteDirectory: '/home/ubuntu/myapp')],
                            execCommand: 'python /home/ubuntu/python/test.py'
                        )
                    ]
                )
            }
        }
    }
}
