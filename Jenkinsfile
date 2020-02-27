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
                sh "ls -al"
                sh "git clone https://github.com/jenkins2020/tk"
                sh "cp tk/hello.spec ~/rpmbuild/SPEC"
            }
        }
        stage('Build') {
            steps {
                sh "cd ~/rpmbuild/SPEC && rpmbuild -ba hello.spec"
            }
        }
    }
}
