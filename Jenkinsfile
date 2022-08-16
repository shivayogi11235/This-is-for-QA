pipeline {
    agent none 
    agent none

    environment {
        BRANCH = 'main'
        GIT_REPO = 'https://github.com/jaintpharsha/devops-june-2022.git'
    }

    stages {
        stage('A') {
            agent any
            environment {
                BUILD_ENV = 'only_for_build_stage'
            }
            steps {
                git branch: 'main', url: 'https://github.com/jaintpharsha/devops-june-2022.git'
                git branch: $BRANCH, url: $GIT_REPO
                sh '''
                    #!/bin/bash 
                    pwd 
                    ls
                    echo "This is a BUILD stage"
                    sleep 5
                    echo "$BUILD_ENV"
                '''  
            }
        }

        stage('TESTING1') {
            agent { label 'slave2' } 
            steps {
                sh 'echo "This is a TESTING1 stage"'
                sh 'sleep 5'
            }
        }

        stage('TESTING2') {
            agent { label 'master' } 
            steps {
                sh '''
                    echo "This is a TESTING2 stage"
                    sleep 5
                '''
                echo "$BRANCH $GIT_REPO"
                echo "$BUILD_ENV"
            }
        }
    }
