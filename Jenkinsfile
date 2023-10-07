pipeline {
    agent { node { label 'AGENT-1' } } 
    environment { 
        USER = 'KLKREDDY'
    }
    options {
        timeout(time: 1, unit: 'HOURS') 
    }
    parameters {
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')

        text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')

        booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')

        choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')

        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
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
        stage('Access') {
            environment { 
                AN_ACCESS_KEY = credentials('ssh-auth') 
            }
            steps {
                sh 'printenv'
            }
        }
        stage('Params') {
            steps {
                echo "Hello ${params.PERSON}"

                echo "Biography: ${params.BIOGRAPHY}"

                echo "Toggle: ${params.TOGGLE}"

                echo "Choice: ${params.CHOICE}"

                echo "Password: ${params.PASSWORD}"
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

