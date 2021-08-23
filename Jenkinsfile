pipeline{
    agent any
    tools {
    maven 'Maven_local'
    }
    stages {
        stage('git_clone') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: 'd2cc9d02-a94a-4678-b837-9181db4f723c', url: 'https://github.com/rushikeshsawant143/node-js-sample.git']]])
                sh 'pwd'
                sh 'docker rmi -f nodeimage'
                sh 'docker container rm -f nodecontainer'
                sh 'docker build -t nodeimage .'
                sh 'docker run -d --name nodecontainer -p 3306:5000 nodeimage'
            }
        }  
    }
}
