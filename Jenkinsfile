pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo "Github Commit Received. Building in Process"
                echo "building code with Java maven. The reason for this is because of increased performance and project code building"
            }
        }
        stage('Test') {
            steps {
                echo "in the testing stage, I am using the JUnit tester. The reason for this is to test the code function and integrations to ensure the application is working as expected"
            }
            post {
                success {
                    mail to: "lachlanmcdonald2000@gmail.com",
                    subject: "Test Email",
                    body: "Test stage complete"
                }
            }
        }
        stage('Code Analysis') {
            steps {
                echo "in the coding analysis stage I am using SonarQube. The reason for this is because it can perform static coding analysis to discover any potential vulnerabilities"
            }
        }
        stage('Security Scan') {
            steps {
                echo "In the security scanning phase, OWASP Dependency-Check is the tool I will be using because it can perform similar functions to SonarQube but also identify any potential vulnerable dependencies"
            }
            post {
                success {
                    mail to: "lachlanmcdonald2000@gmail.com",
                    subject: "Security Scan Email",
                    body: "Security Stage stage complete"
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo "deploy to staging environment requires no tools for this process"
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo "for the integration testing stage, we write test cases to ensure different components of the application are working together correctly"
            }
        }
        stage('Deploy to Production') {
            steps {
                echo "if everything is successful up to this point, we deploy the code to production"
            }
        }
    }
}
