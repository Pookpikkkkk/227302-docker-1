pipeline {
    agent any

    stages {
        stage('Pull Docker Image') {
            steps {
                echo 'Waiting for service to initialize...' 
                sleep time: 120, unit: 'SECONDS'
                script {
                    sh '''docker pull apinyasanghong/my-image-09122025:main'''
                }
            }
        }
        stage('Run Docker Container') {
            steps {
                script {
                    sh '''
        
                    if [ "$(docker ps -aq -f name=^/67023008$)" ]; then
                        echo "Found container '67023008'. Restarting..."
                        docker restart 6703008
                    else
                        echo "Container '67023008' not found."
                        docker run --rm -p 3008:3000 --name 67023008 -d  apinyasanghong/my-image-09122025:main
                    fi
                    '''
                }
            }
        }
    }
}