pipeline {
    agent any
    environment{
        PATH= "/opt/apache-maven-3.9.0/bin:$PATH"
    }
    stages {
        stage("welcome") {
            steps{
                echo "welcome to the declarative jenkins pipeline "
            }
        }
        stage("git clone") {
            steps{
                git branch: 'main', url: 'https://github.com/praveenakumara/excercise.git'
            }
        }
        stage("maven build") {
            steps{
                sh "mvn clean install"
            }
        }
        stage("deploy-dev") {
            steps{
            deploy adapters: [tomcat9(credentialsId: 'ffba2c34-7718-428b-ad2a-c737abb51796', path: '', url: 'http://3.109.62.210:8080')], contextPath: 'praveen', war: '**/*.war'    
            }
        }
    }
}
