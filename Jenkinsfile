pipeline {
    agent any
    
    tools{
        //Install the Maven version configured as "M3" and add it to the path 
        maven "M3"
        
    }
    
    stages {
        stage('Checkout'){
            steps {
                //Get some code from a Github repository
                git branch:'main',url:'https://github.com/nimz19/lbg-hello-world-maven.git'
            }
        }
        stage('Compile') {
            steps{
                //Run Maven on Unix agent
                sh "mvn clean compile"
            }
        }
        stage('Test') {
            steps {
                sh "mvn -Dmaven.compile.skip test"
            }
        }
        stage('Package') {
            steps {
                sh "mvn -Dmaven.test.skip -Dmaven.compile.skip package"
            }
        }
    }
}