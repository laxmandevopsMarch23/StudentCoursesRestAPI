pipeline {
    agent { label 'docker' }
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
    }

}