pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Stage 1: Building'
                sh 'mvn clean package'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'Stage 2: Running unit and integration tests'
                sh 'mvn test'
                sh 'mvn integration-test'
            }
        }
        stage('Code Analysis') {
            steps {
                echo 'Stage 3: Running code analysis'
                withSonarQubeEnv('SonarQube') {
                    sh 'mvn sonar:sonar'
                }
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Stage 4: Performing security scan'
                sh 'zap-baseline.py -t http://your-app-url'
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo 'Stage 5: Deploying to staging'
                sh 'deploy-to-staging.sh'
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo 'Stage 6: Running integration tests on staging'
                sh 'mvn integration-test -DstagingEnvironment=true'
            }
        }
        stage('Deploy to Production') {
            steps {
                echo 'Stage 7: Deploying to production'
                sh 'deploy-to-production.sh'
            }
        }
    }
    post {
        success {
            echo 'Pipeline succeeded.'
            emailext subject: "Pipeline Success: ${currentBuild.fullDisplayName}",
                      body: "The Jenkins pipeline ran successfully.",
                      to: "ubaid.a218@gmail.com"
        }
        failure {
            echo 'Pipeline failed.'
            emailext subject: "Pipeline Failure: ${currentBuild.fullDisplayName}",
                      body: "The Jenkins pipeline failed. Check the logs for details.",
                      to: "ubaid.a218@gmail.com"
        }
    }
}
