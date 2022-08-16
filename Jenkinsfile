def FAILED_STAGE

pipeline {
    agent any
    stages {
        stage("A") {
            steps {
                script {
                    FAILED_STAGE=true
                    echo "stage 1"
                }
            }
        }
        stage("B") {
            when{
                FAILED_STAGE==false 
            }
            steps {
                script {
                    echo "stage 2"
                    
                }
            }
        }
        stage("C") {
            steps {
                when{
                    FAILED_STAGE==true
                }
                script {
                    
                    echo "stage 3"
                }
            }
        }
    }
}    
