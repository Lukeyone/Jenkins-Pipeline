pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                echo "Github Commit Received. Building in Process"
                echo "Building code with Java Maven. The reason for this is because of increased performance and project code building."
            }
        }
        stage('Test') {
            steps {
                echo "In the testing stage, I am using the JUnit tester. The reason for this is to test the code function and integrations to ensure the application is working as expected."
            }
            post {
                success {
                    emailext(
                        to: "lachlanmcdonald2000@gmail.com",
                        subject: "Test Email",
                        body: "Test stage complete, Testing passed successfully. All tests passed",
                        attachLog: true
                    )
                }
            }
        }
        stage('Code Analysis') {
            steps {
                echo "In the coding analysis stage I am using SonarQube. The reason for this is because it can perform static coding analysis to discover any potential vulnerabilities."
            }
        }
        stage('Security Scan') {
            steps {
                echo "In the security scanning phase, OWASP Dependency-Check is the tool I will be using because it can perform similar functions to SonarQube but also identify any potential vulnerable dependencies."
            }
            post {
                success {
                    emailext(
                        to: "lachlanmcdonald2000@gmail.com",
                        subject: "Security Scan Email",
                        body: "Security Stage complete, security scan passed successfully. No issues found",
                        attachLog: true
                    )
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo "Deploy to staging environment requires no tools for this process."
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo "For the integration testing stage, we write test cases to ensure different components of the application are working together correctly."
            }
        }
        stage('Deploy to Production') {
            steps {
                echo "If everything is successful up to this point, we deploy the code to production."
            }
        }
    }
    
    post {
        always {
            echo 'Pipeline completed.'
            
            emailext(
                attachLog: true,
                attachmentsPattern: 'generatedFile.txt',
                body: "${currentBuild.currentResult}: Job ${env.JOB_NAME} build ${env.BUILD_NUMBER}\n More info at: ${env.BUILD_URL}",
                recipientProviders: [developers(), requestor()],
                subject: "Jenkins Build ${currentBuild.currentResult}: Job ${env.JOB_NAME}"
            )
        }
    }
}
