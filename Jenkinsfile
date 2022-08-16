def flag=false


pipeline {
    agent any
    
    stages {
        stage('A') {
            steps {
		    echo "insie block A"	
                 script { flag = true }
                }
            }
       
            
        stage('B') {
		when{
		expression {flag==false}
		}
            	steps {
                script{
                   
                        echo " executing Stage B"
                   
                }
            }
        }
        
        stage('C') {
		when{
		expression {flag==true}
		}
            steps {
                    echo "executing Stage C"
            }
        }
    }
}
