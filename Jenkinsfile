pipeline {
    agent { label 'AGENT-1' }
    
    options {
        timeout(time: 2, unit: 'MINUTES')  
        disableConcurrentBuilds()
    }
    
    parameters {
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
        text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')
        booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')
        choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')
        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password') 
    }
    
    environment {
        DEPLOY_TO = 'production'
        GREETING = 'Good Morning'
    }
    
    stages {
        stage ('SCM Checkout') {
            steps {
                sh 'echo scm checkout stage'
            }
        }
        stage('Build & Compile') {  
            steps {
                sh 'echo This is build'
                sh 'env'
            }
        }
        stage ('Package') { 
            steps {
                sh 'echo Build stage is success!!!!'
            }
        }
        
        stage ('Test') {
            steps {
                sh 'echo Test stage is success!!!!'
            }
        }
        
        stage ('Deploy') {
            steps {
                sh 'echo Deploy stage is success!!!!'
            }
        }
        
        stage("Print Parameters") {
            steps {
                echo "Hello ${params.PERSON}"
                echo "Biography: ${params.BIOGRAPHY}"
                echo "Toggle: ${params.TOGGLE}"
                echo "Choice: ${params.CHOICE}"
                echo "Triggered test again"
                echo "Password: ******** (masked)" 
            }
        }
    }
    
    post {  
        always { 
            echo 'I will always say Hello again!'
        }
        success { 
            echo 'I will run when pipeline is successful'
        }
        failure { 
            echo 'I will run when pipeline fails'
        }
    }
}

