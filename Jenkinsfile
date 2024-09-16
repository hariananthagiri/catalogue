pipeline {
    agent { 
        node { 
            label 'AGENT-1' 
        } 
    }
    environment {
        GREETING = "hello jenkins"
    }
    // build
    stages {
        stage('Build') {
            steps {
                echo 'Building....'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing....'
            }
        } 

        stage('Environment') {
            steps {
                echo "using environment variable"
                sh '''
                echo "${GREETING}"
                '''
            }
        } 
        stage('Deploy') {
            input {
                message "should we continue?"
                ok "yes, we should." 
            }
            steps {
                echo 'Deploying....'
                sh '''
                    ls -ltr
                    pwd
                '''
            }
        }
    }
    // post build
    post { 
        always { 
            echo 'It will run whethere job is sucess or not'
            deleteDir()
        }
        success { 
            echo 'It will run whethere job is sucess'
        }
        failure { 
            echo 'It will run whethere job is failure'
        }    
    }     
}
