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
        withCredentials([string(credentialsId: 'ab234bd7-ac71-4eb5-a9a3-778c570b2a89', variable: 'DHPWD')]) 
        {
            sh "docker login -u dogiparthy85 -p ${DHPWD}"
        }
        sh 'docker push dogiparthy85/online-shop'
    }
}
