pipeline {
    agent any
    
    tools {
        maven 'Maven' 
    }
    
    stages {
        stage("Test") {
            steps {
                // mvn test
                bat "mvn test"
            }
        }
        
        stage("Build") {
            steps {
                bat "mvn build"
            }
        }
        
        stage("Deploy on Test") {
            steps {
                // deploy on container -> plugin
                deploy adapters: [tomcat9(credentialsId: 'tomcat9details', path: '', url: 'http://localhost:8080')], contextPath: '/app', war: '**/*.war'
            }
        }
        
        stage("Deploy on Prod") {
            input {
                message "Should we continue?"
                ok "Yes we Should"
            }
            
            steps {
                // deploy on container -> plugin
                deploy adapters: [tomcat9(credentialsId: 'tomcat9details', path: '', url: 'http://localhost:8080')], contextPath: '/app', war: '**/*.war'
            }
        }
    }
    
    post {
        always {
            echo "========always========"
        }
        
        success {
            echo "========pipeline executed successfully ========"
        }
        
        failure {
            echo "========pipeline execution failed========"
        }
    }
}
