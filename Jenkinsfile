pipeline {
    agent none
    stages {
        stage('Build Web') {
            agent {
                docker {
                    image 'node:lts-bullseye-slim'
                    args '-p 3000:3000'
                }
            }
            when {
                changeset "**/web/*.*"
                beforeAgent true
            }
            steps {
                build job: 'Web', propagate: true
            }
        }
        stage('Build iOS') {
            agent {
                docker {
                    image 'node:lts-bullseye-slim'
                    args '-p 3000:3000'
                }
            }
            when {
                changeset "**/app/ios/*.*"
                beforeAgent true
            }
            steps {
               build job: 'iOS', propagate: true
            }
        }
        stage('Build Android') {
            agent {
                docker {
                    image 'node:lts-bullseye-slim'
                    args '-p 3000:3000'
                }
            }
            when {
                changeset "**/app/android/*.*"
                beforeAgent true
            }
            steps {
               build job: 'Android', propagate: true
            }
        }
    }
}