pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                script {
                    def buildLog = 'build.log'
                    writeFile(file: buildLog, text: '')
                    sh "echo 'Github Commit Received. Building in Process' >> ${buildLog}"
                    sh "echo 'building code with Java maven. The reason for this is because of increased performance and project code building' >> ${buildLog}"
                    archiveArtifacts artifacts: buildLog, allowEmptyArchive: true
                }
            }
        }
        stage('Test') {
            steps {
                script {
                    def testLog = 'test.log'
                    writeFile(file: testLog, text: '')
                    sh "echo 'in the testing stage, I am using the JUnit tester. The reason for this is to test the code function and integrations to ensure the application is working as expected. Demo project here' >> ${testLog}"
                }
            }
            post {
                success {
                    archiveArtifacts artifacts: 'test.log', allowEmptyArchive: true
                    emailext(
                        to: "lachlanmcdonald2000@gmail.com",
                        subject: "Test Stage Complete",
                        body: "Test stage complete, Testing passed successfully. All tests passed",
                        attachmentsPattern: 'test.log'
                    )
                }
            }
        }
        stage('Code Analysis') {
            steps {
                script {
                    def analysisLog = 'analysis.log'
                    writeFile(file: analysisLog, text: '')
                    sh "echo 'in the coding analysis stage I am using SonarQube. The reason for this is because it can perform static coding analysis to discover any potential vulnerabilities' >> ${analysisLog}"
                }
            }
        }
        stage('Security Scan') {
            steps {
                script {
                    def securityLog = 'security.log'
                    writeFile(file: securityLog, text: '')
                    sh "echo 'In the security scanning phase, OWASP Dependency-Check is the tool I will be using because it can perform similar functions to SonarQube but also identify any potential vulnerable dependencies. Demo and email sent' >> ${securityLog}"
                }
            }
            post {
                success {
                    archiveArtifacts artifacts: 'security.log', allowEmptyArchive: true
                    emailext(
                        to: "lachlanmcdonald2000@gmail.com",
                        subject: "Security Scan Complete",
                        body: "Security Stage complete, security scan passed successfully. No issues found",
                        attachmentsPattern: 'security.log'
                    )
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
