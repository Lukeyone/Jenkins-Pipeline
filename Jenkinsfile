pipeline {
    agent any
 
    stages {
        stage('Build') {
            steps {
                echo 'Stage 1: Build'
		echo 'Detail: Build code using build'
                echo 'Build Automation Tool: Maven ig .......'
            }
        }
 
        stage('Unit and Integration Tests') {
            steps {
                echo 'Stage 2: Unit and Integration Tests'
		echo 'Detail: Run '
                echo 'Test Automation Tool: Junit 5'
            }
            post {
                success {
                    emailext(
			    	attachLog: true, 
				to: 'lachlanmcdonald2000@gmail.com',
				subject: 'Unit and Integration Test: Successful', 
				body: 'Stage 2 successfully implemented. Refer Report.'
			    )
                	}
                failure {
                    emailext(
			    	attachLog: true, 
				to: 'lachlanmcdonald2000@gmail.com',
				subject: 'Unit and Integration Test: Failure', 
				body: 'Stage 2 unsuccessfully implemented. Refer Report.' 
			    )
                	}
            	}
        }
 
        stage('Code Analysis') {
            steps {
                echo 'Stage 3: Code Analysis'
		echo 'Detail: Analyse code '
                echo 'Code Analysis Tool: SonarQube is used'
            }
        }
 
        stage('Security Scan') {
            steps {
                echo 'Stage 4: Security Scan'
		echo 'Detail: Perform se'
                echo 'Security Scan Tool: OWASP Security Tool '
            }
            post {
                success {
                    emailext(
			    	attachLog: true, 
				to: 'lachlanmcdonald2000@gmail.com',
				subject: 'Security Scan Test: Successful', 
				body: 'Stage 4 successfully implemented. Refer Report.' 
			    )
                	}
                failure {
                    emailext( 
			    	attachLog: true, 
				to: 'lachlanmcdonald2000@gmail.com',
				subject: 'Security Scan Test: Failure', 
				body: 'Stage 4 unsuccessf.' 
			    )
                	}
            	}
        }
 
        stage('Deploy to Staging') {
            steps {
                echo 'Stage 5: Deploy to Staging'
		echo 'Detail: Deploy appli'
            }
        }
 
        stage('Integration Tests on Staging') {
            steps {
                echo 'Stage 6: Integration Tests on Staging'
		echo 'Detail: Conduct i'
            }
        }
 
        stage('Deploy to Production') {
            steps {
                echo 'Stage 7: Deploy to Production'
		echo 'Detail: Deploy appli'
            }
        }
    }
}
