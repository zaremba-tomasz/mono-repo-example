pipeline {
    agent none
    stages {
        stage('Build Web') {
            when {
                changeset "**/web/*.*"
                beforeAgent true
            }
            steps {
                build job: 'Web', propagate: true, wait: false
            }
        }
        stage('Build iOS') {
            when {
                changeset "**/app/ios/*.*"
                beforeAgent true
            }
            steps {
               build job: 'iOS', propagate: true, wait: false
            }
        }
        stage('Build Android') {
            when {
                changeset "**/app/android/*.*"
                beforeAgent true
            }
            steps {
               build job: 'Android', propagate: true, wait: false
            }
        }
    }
}