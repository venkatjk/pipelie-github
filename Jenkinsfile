pipeline {
    agent any
  
    environment {
        course = "Java"
    }
    parameters {
        string(name: 'username',defaultValue: 'Devops', description: "who are you?")
        string(name: 'phonenumber',defaultValue: '12323', description: "User phone number")
        booleanParam(name: 'male',defaultValue: 'person', description: "")
        choice(name: 'Env',choices:['DEV','TEST','UAT','PROD'],description: "")
    }
    
    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
                sh 'echo $course'
                sh 'echo $username'
                sh 'echo $male'
                sh 'echo The environment you selected $Env'
            }
            post { 
             success { 
                echo 'success'
                 }
              }
            
        }
        stage('Build') {
            steps {
                echo 'Build stage'
                sh '''
                date
                ls -l /tmp
                cal
                '''
                 sh 'echo $course'
                 sh 'echo ${phonenumber}'
            }
            post { 
             success { 
                echo 'success stage 2'
                 }
              }
        }
        stage('Env') {
            environment {
                     name = "venkat"
                 }
            steps {
                sh '''
                echo ${BUILD_ID}
                echo ${BUILD_DISPLAY_NAME}
                echo ${JOB_BASE_NAME}
                '''
                 sh 'echo $course'
                 sh 'echo $name'
                
                 
            }
            post { 
             success { 
                echo 'success 3'
                 }
              }
        }
        stage('DEV') {
            steps {
                echo 'Deploy to DEV server'
             
            }
        }
           stage('PROD') {
               input {
                   message "should we continue"
                   ok "yes"
               }
            steps {
                echo 'Deploy to PROD server'
               
            }
            post { 
             success { 
                echo 'success 4'
                 }
              }
        }
    }
    post { 
        success { 
            echo 'I will always say Hello again!'
        }
    }
}
