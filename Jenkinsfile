pipeline{
    agent any
    tools {
        maven 'Maven'
    }
    stages{
        stage("Test"){
            steps{
                // mvn test
                sh "mvn test"
            }
        }
         stage("Build"){
            steps{
                "mvn package"
            }
        }
         stage("Deploy on test"){
            steps{
                // deploy on container -> plugin
                deploy adapters: [tomcat9(credentialsId: 'forjenkinsfile', path: '', url: 'http://192.168.0.116:8000')], contextPath: '/app', war: '**/*.war'
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
