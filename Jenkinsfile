pipeline {
    agent any
    
    tools {
        // Install the Maven version configured as "M3" and add it to the path 
        maven "M3"
    }
    
    stages {
        stage('Checkout') {
            steps {
                // Get some code from a Github repository
                git branch: 'main', url: 'https://github.com/nimz19/lbg-hello-world-maven.git'
            }
        }
        stage('Compile') {
            steps {
                // Run Maven on Unix agent to clean and compile
                sh "mvn clean compile"
            }
        }
        stage('Test') {
            steps {
                // Run tests and skip the compile step
                sh "mvn -Dmaven.compile.skip test"
            }
        }
        stage('Package') {
            steps {
                // Skip tests and compile, then package the application
                sh "mvn -Dmaven.test.skip clean package"
            }
        }
        stage('Run Java Application') {
            steps {
                // Run the compiled Java class from the target directory
                sh "java -cp target/classes com.qa.App"
            }
        }
    }
}
