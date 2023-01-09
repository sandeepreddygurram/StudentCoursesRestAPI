pipeline {
    agent { label 'NODE1' }
    triggers { pollSCM('* * * * *') }
    stages {
        stage('vcs') {
            steps {
                git branch: 'develop',
                    url: 'https://github.com/srikanth458/StudentCoursesRestAPI.git'
            }
        }
        stage('build and deploy') {
            steps {
                sh 'docker image build -t srikanth458/courses .'
                sh 'docker image push srikanth458/courses'
            }
        }
        

    }
}
