pipeline{
    agent any
    tools {
        maven 'Maven' 
    }
    stages{
        stage("Test"){
            steps{
                sh "mvn test"
                echo "========executing A========"
            }
        }
        stage("Build"){
            steps{
                sh "mvn package"
                echo "========executing A========"
            }
        }
        stage("Deploy on Test"){
            steps{
                // deploy on container -> plugin
                deploy adapters: [tomcat9(credentialsId: 'tomcatserverdetails1', path: '', url: 'http://43.205.117.168:8080')], contextPath: '/app', war: '**/*.war'
                echo "========executing A========"
            }
        }
        stage("Deploy on Pod"){
            steps{
                // deploy on container -> plugin
                deploy adapters: [tomcat9(credentialsId: 'tomcatserverdetails1', path: '', url: 'http://65.2.10.189:8080')], contextPath: '/app', war: '**/*.war'
                echo "========executing A========"
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
