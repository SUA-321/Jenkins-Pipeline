pipeline {
    agent any
    stages{
        stage("Build"){
            steps{
                echo "Building..."
            }
            post{
                always{
                    mail to: "ubaid.a218@gmail.com",
                    subject: "Build Status Email",
                    body: "Build was Successful!"
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
        stage("Completed"){
            steps{
                echo "Build Completion"
            }
        }
    }
}
