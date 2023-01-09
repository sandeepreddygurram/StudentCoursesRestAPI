pipeline {
    agent { label 'k8s' }
    triggers { pollSCM('* * * * *') }
    stages {
        stage('vcs') {
            steps {
                git branch: 'develop',
                    url: 'https://github.com/sandeepreddygurram/StudentCoursesRestAPI.git'
            }
        }
        stage('build and deploy') {
            steps {
                sh 'docker image build -t 8465824520/courses .'
                sh 'docker image push 8465824520/courses'
            }
        }
        stage('deploy') {
            agent {label 'k8s'}
            steps {
                sh 'kubectl apply -f deploy.yaml'
                sh 'kubectl apply -f rs.yaml'
            }
        }

    }
}
