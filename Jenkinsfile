pipeline {
    agent none
    stages {
        stage('Build Web') {
            when {
                anyOf {
                    changeset "**/web/*.*"
                    expression { currentBuild.number == 1 }
                }
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
                    expression { currentBuild.number == 1 }
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
                    expression { currentBuild.number == 1 }
                }
            }
            steps {
               build job: 'Android', propagate: true, wait: false
            }
        }
    }
}