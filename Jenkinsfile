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

stage('Run Nginx Load Balancer') {
    steps {
        sh '''
        docker rm -f nginx-lb || true

        docker run -d --name nginx-lb --network lab-net -p 80:80 nginx

        sleep 3

        docker cp nginx/default.conf nginx-lb:/etc/nginx/conf.d/default.conf
        docker exec nginx-lb nginx -s reload
        '''
    }
}

