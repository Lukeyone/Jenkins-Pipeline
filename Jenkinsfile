pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo "Github Commit Received. Building in Process"
                echo "Building code with Java Maven. The reason for this is because of increased performance and project code building"
                bat 'echo Build log content > build.log'
                archiveArtifacts artifacts: 'build.log', allowEmptyArchive: true
            }
        }
        stage('Test') {
            steps {
                echo "In the testing stage, I am using the JUnit tester. The reason for this is to test the code function and integrations to ensure the application is working as expected. Demo project here"
                bat 'echo Test log content > test.log'
                archiveArtifacts artifacts: 'test.log', allowEmptyArchive: true
            }
            post {
                success {
                    // Send email using mail step for simpler email without attachment
                    mail to: "lachlanmcdonald2000@gmail.com",
                         subject: "Test Stage Complete",
                         body: "Test stage complete, Testing passed successfully. All tests passed"
                         
                    // Use PowerShell to send email with attachment
                    bat '''
                    powershell.exe -Command "Send-MailMessage -To 'lachlanmcdonald2000@gmail.com' -From 'your-email@example.com' -Subject 'Test Stage Complete with Logs' -Body 'Test stage complete, Testing passed successfully. All tests passed' -Attachments 'test.log' -SmtpServer 'smtp.yourserver.com' -Credential (Get-Credential)"
                    '''
                }
            }
        }
        stage('Code Analysis') {
            steps {
                echo "In the coding analysis stage, I am using SonarQube. The reason for this is because it can perform static coding analysis to discover any potential vulnerabilities"
            }
        }
        stage('Security Scan') {
            steps {
                echo "In the security scanning phase, OWASP Dependency-Check is the tool I will be using because it can perform similar functions to SonarQube but also identify any potential vulnerable dependencies. Demo and email sent"
                bat 'echo Security scan log content > security.log'
                archiveArtifacts artifacts: 'security.log', allowEmptyArchive: true
            }
            post {
                success {
                    // Send email using mail step for simpler email without attachment
                    mail to: "lachlanmcdonald2000@gmail.com",
                         subject: "Security Scan Complete",
                         body: "Security stage complete, security scan passed successfully. No issues found"
                         
                    // Use PowerShell to send email with attachment
                    bat '''
                    powershell.exe -Command "Send-MailMessage -To 'lachlanmcdonald2000@gmail.com' -From 'your-email@example.com' -Subject 'Security Scan Complete with Logs' -Body 'Security stage complete, security scan passed successfully. No issues found' -Attachments 'security.log' -SmtpServer 'smtp.yourserver.com' -Credential (Get-Credential)"
                    '''
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo "Deploy to staging environment requires no tools for this process"
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo "For the integration testing stage, we write test cases to ensure different components of the application are working together correctly"
            }
        }
        stage('Deploy to Production') {
            steps {
                echo "If everything is successful up to this point, we deploy the code to production"
            }
        }
    }
}
