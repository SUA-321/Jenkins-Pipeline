pipeline {
    agent any
    stages{
        stage("Build"){
            steps{
                echo "Building..."
            }
            post {
               always {
                  script {
                     def emailSubject = "Build Status Email"
                     def emailBody = "Build log attached!"
                       def recipientEmail = "ubaid.a218@gmail.com"

                       // Create the email attachment
                       def message = "${emailBody}\n\n${currentBuild.rawBuild.getLog()}" 

                    mail to: recipientEmail,
                    subject: emailSubject,
                    body: message
            }
        }
    }
        }
        stage("Test"){
            steps{
                echo "Testing..."
            }
        }
        stage("Deploy"){
            steps{
                echo "Deploying..."
            }
        }
    }
}
