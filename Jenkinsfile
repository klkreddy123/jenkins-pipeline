pipeline {
    agent { node { label 'AGENT-1' } } 
    environment { 
        USER = 'KLKREDDY'
    }
    options {
        timeout(time: 1, unit: 'HOURS') 
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
                sh 'ls -ltr'
                sh 'pwd'
                sh'''
                    ls -ltr
                    pwd
                    printenv
                '''
                echo "Hello from github push webhook event"
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
               // error 'this is failure'
            }
        }
    }
    post { 
        
        always { 
            echo 'I will always run whether job is success or not'
        }

        success { 
            echo 'I will only run when job is success'
        }
            
        failure { 
            echo 'I will run when failure'
        }
        
    }
}

