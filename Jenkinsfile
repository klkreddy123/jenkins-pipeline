pipeline {
    agent { node { label 'AGENT-1' } } 
        // triggers {
        // cron('0 * * * *')
        // }
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
    stage('Appro') {
            input {
                message "Should we continue?"
                ok "Yes, we should."
                submitter "alice,bob"
                parameters {
                    string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
                }
            }
            steps {
                echo "Hello, ${PERSON}, nice to meet you."
            }
        }
    stage('Approval') {
            input {
                message "Should we continue?"
                ok "Yes, we should."
                submitter "alice,bob"
                parameters {
                    string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
                }
            }
            steps {
                echo "Hello, ${PERSON}, nice to meet you."
            }
        }
         stage('Prod Deploy') {
            when {
                branch 'master'
            }
            steps{
                echo "deploying to Prod"
            }
    //     stage('Parallel Stage') {
    //         parallel {
    //             stage('Branch A') {

    //                 steps {
    //                     echo "On Branch A"
    //                     sleep 20
    //                 }
    //             }
    //             stage('Branch B') {

    //                 steps {
    //                     echo "On Branch B"
    //                     sleep 20
    //                 }
    //             }
    //             stage('Branch C') {

    //                 stages {
    //                     stage('Nested 1') {
    //                         steps {
    //                             echo "In stage Nested 1 within Branch C"
    //                             sleep 20
    //                         }
    //                     }
    //                     stage('Nested 2') {
    //                         steps {
    //                             echo "In stage Nested 2 within Branch C"
    //                             sleep 20
    //                         }
    //                     }
    //                 }
    //             }
    //         }
    // }
    
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
}
