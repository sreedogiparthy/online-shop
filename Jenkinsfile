node{

    stage('SCM Checkout')
    {
        git credentialsId: '8d151821-1af4-43ec-9dec-c2a847e48e23', url: 'https://github.com/dogiparthy85/online-shop.git'
    }
    
    stage('Run Docker Compose File')
    {
        sh 'docker-compose build'
        sh 'docker-compose up -d'
    }
    stage('PUSH image to Docker Hub')
    {
        withCredentials([string(credentialsId: 'DockerHubPassword', variable: 'DHPWD')]) 
        {
            sh "docker login -u vardhanns -p ${DHPWD}"
        }
        sh 'docker push dogiparthy85/online-shop'
    }
}
