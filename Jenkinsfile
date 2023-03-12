pipeline {
    agent { label 'UBUNTU-ID' }
    triggers { 
        pollSCM('* * * * *')
    }
    stages {
        stage('vcs') {
            steps {
                git url: 'https://github.com/laxmandevopsMarch23/StudentCoursesRestAPI.git',
                    branch: 'develop'
            }
        }
        stage('build') {
            steps {
                sh 'docker image build -t laxmangottipati/spc:latest .'
            }
        }
        stage('scan and push') {
            steps {
                sh 'echo docker scan laxmangottipati/spc:latest'
                sh 'docker image push laxmangottipati/spc:latest'
            }
        }
        stage('deploy to st') {
            steps {
                sh 'kubectl apply -f ./K8s/mysql-aws.yml'
                sh 'kubectl apply -f ./K8s/flask-aws.yml'
                sh 'sleep 10s'
                sh 'kubectl get svc'
            }
        }
    }

}