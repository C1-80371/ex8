pipeline {
    agent any
    
    stages {
        stage ('SCM') {
            steps {
                git 'https://github.com/C1-80371/ex8.git'
            }
        }
        
        stage ('Docker login') {
            steps {
                sh 'echo dckr_pat_88Gj9d2Pbi6xUqcILl68YM9wngA | /usr/bin/docker login -u kuldeeproy --password-stdin'
            }
        }
        
        stage ('Docker build image') {
            steps {
                sh '/usr/bin/docker build -t kuldeeproy/httpd1 .'
            }
        }
        
        stage ('Docker image push') {
            steps {
                sh '/usr/bin/docker image push kuldeeproy/httpd1'
            }
        }
        
        stage ('Remove service') {
            steps {
                sh '/usr/bin/docker service rm myservice'
            }
        }
        
        stage ('Create service') {
            steps {
                sh '/usr/bin/docker service create --name myservice --replicas 5 kuldeeproy/httpd1'
            }
        }
    }
}
