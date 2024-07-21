pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout the 'main' branch
                git branch: 'main', url: 'https://github.com/Littlesens/Jenkins_test.git'
            }
        }
        stage('Build') {
            steps {
                echo 'Building...'
                // Add build steps here, e.g., compile code, download dependencies, etc.
                // For example, if you are using Maven:
                // sh 'mvn clean install'
            }
        }
        stage('OWASP Dependency-Check Vulnerabilities') {
     steps {
       dependencyCheck additionalArguments: '''
                   -o './'
                   -s './'
                   -f 'ALL'
                   --prettyPrint''', odcInstallation: 'OWASP Dependency-Check Vulnerabilities'
      
       dependencyCheckPublisher pattern: 'dependency-check-report.xml'
     }
   }
        stage('Test') {
            steps {
                echo 'Testing...'
                // Add testing steps here, e.g., run unit tests, integration tests, etc.
                // For example, if you are using Maven:
                // sh 'mvn test'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying...'
                // Add deployment steps here, e.g., deploy to a staging environment, production, etc.
                // For example, if you are deploying to a server:
                // sh 'scp target/my-app.jar user@server:/path/to/deploy'
            }
        }
    }
}
