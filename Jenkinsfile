pipeline {
    agent any
    stages {
        stage ('git pull') {
            steps {
                git credentialsId: 'git', url: 'https://github.com/Mr3lack/onlinebookstore.git'
                sh 'ls -lrt'
            }
        }
        stage ('build') {
            steps {
                sh 'mvn clean install'
            }
            
        }
        stage ('deploy') {
            steps {
                sh 'chmod 400 jenkins.pem'
                sh 'scp -i jenkins.pem -o StrictHostKeyChecking=no -P 22 target/online*.war root@13.201.52.102:/opt/tomcat/webapps/onlinebookstore.war'
            }
        }
    }
}
