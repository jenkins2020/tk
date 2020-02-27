pipeline {
    agent {
        dockerfile {
            filename 'Dockerfile'
        }
    }
    stages {
        stage('Init') {
            steps {
                sh "rpmdev-setuptree"
                sh "ls ~/rpmbuild/*"
            }
        }
        stage('GetSource') {
            steps {
                sh "cd ~/rpmbuild/SOURCES && wget http://ftp.gnu.org/gnu/hello/hello-2.10.tar.gz"
            }
        }
        stage('GetSpec') {
            steps {
                sh "cp hello.spec ~/rpmbuild/SPECS"
            }
        }
        stage('Build') {
            steps {
                sh "cd ~/rpmbuild/SPECS && rpmbuild -ba hello.spec"
            }
        }
    }
    post {
        always {
            archiveArtifacts artifacts: '/home/user/rpmbuild/**/*.rpm', fingerprint: true
        }
    }
}
