pipeline {
    agent none
    stages {
        stage('Build Web') {
            when {
                changeset "**/web/*.*"
            }
            steps {
                build job: 'Web', propagate: true, wait: false
            }
        }
        stage('Build iOS') {
            when {
                anyOf {
                    changeset "**/app/ios/*.*"
                    changeset "**/app/shared.txt"
                }
            }
            steps {
               build job: 'iOS', propagate: true, wait: false
            }
        }
        stage('Build Android') {
            when {
                anyOf {
                    changeset "**/app/android/*.*"
                    changeset "**/app/shared.txt"
                }
            }
            steps {
               build job: 'Android', propagate: true, wait: false
            }
        }
    }
}