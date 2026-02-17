stage('Run Backend Containers') {
    steps {
        sh '''
        docker network create lab-net || true

        docker rm -f backend1 backend2 || true

        docker run -d --name backend1 --network lab-net backend-app
        docker run -d --name backend2 --network lab-net backend-app
        '''
    }
}
