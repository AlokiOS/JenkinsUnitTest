pipeline {
    agent any
    stages {
        stage('Build'){
            steps{
                sh "xcodebuild build -project JenkinsUnitTest.xcodeproj -scheme JenkinsUnitTest"
                echo "build succesfully"
            }
        }
        stage('Test'){
            steps{
                echo "build succesfully"
            }
       }
    }
}