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
    }
}
