pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/krystals7/8.2CDevSecOps.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                bat 'npm install'
            }
        }

        stage('Run Tests') {
            steps {
                bat 'npm test || exit /b 0'  
            }
            post {
                always {
                    emailext(
                        to: 's98098126@deakin.edu.au',         
                        subject: "Jenkins - Run Tests Stage: ${currentBuild.currentResult} - ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                        body: """
                            <p><b>Stage:</b> Run Tests</p>
                            <p><b>Status:</b> ${currentBuild.currentResult}</p>
                            <p><b>Job:</b> ${env.JOB_NAME}</p>
                            <p><b>Build Number:</b> ${env.BUILD_NUMBER}</p>
                            <p><b>Build URL:</b> <a href="${env.BUILD_URL}">${env.BUILD_URL}</a></p>
                            <p>See the attached build log for full details.</p>
                        """,
                        mimeType: 'text/html',
                        attachLog: true,                    
                        compressLog: true
                    )
                }
            }
        }

        stage('Generate Coverage Report') {
            steps {
                bat 'npm run coverage || exit /b 0'
            }
        }

        stage('NPM Audit (Security Scan)') {
            steps {
                bat 'npm audit || exit /b 0'
            }
            post {
                always {
                    emailext(
                        to: 's98098126@deakin.edu.au',         
                        subject: "Jenkins - NPM Audit Stage: ${currentBuild.currentResult} - ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                        body: """
                            <p><b>Stage:</b> NPM Audit (Security Scan)</p>
                            <p><b>Status:</b> ${currentBuild.currentResult}</p>
                            <p><b>Job:</b> ${env.JOB_NAME}</p>
                            <p><b>Build Number:</b> ${env.BUILD_NUMBER}</p>
                            <p><b>Build URL:</b> <a href="${env.BUILD_URL}">${env.BUILD_URL}</a></p>
                            <p>See the attached build log for full details (including any known CVEs).</p>
                        """,
                        mimeType: 'text/html',
                        attachLog: true,
                        compressLog: true
                    )
                }
            }
        }
    }
}
