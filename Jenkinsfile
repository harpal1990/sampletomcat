pipeline{
    agent any
    tools {
        maven 'Maven' 
    }

    stages{
        stage("Project-Test"){
            steps{
                sh "mvn test"
            }
            
        }

        stage("Project-Build"){
            steps{
                sh "mvn package"
            }
            
        }

        stage("Project-Deploy-Stage"){
            steps{
                deploy adapters: [tomcat9(credentialsId: 'latestcred', path: '', url: 'http://54.91.86.53:8080')], contextPath: '/techserver', war: '**/*.war' 
            }
            
        }

        stage("Project-Deploy-Prod"){
            steps{
                deploy adapters: [tomcat9(credentialsId: 'latestcred', path: '', url: 'http://52.23.238.138:8080')], contextPath: '/techserver', war: '**/*.war'
              
            }
            
        }
    }
    post{
        always{
            echo "========always========"
        }
        success{
            echo "========pipeline executed successfully ========"
        }
        failure{
            echo "========pipeline execution failed========"
        }
    }
}
