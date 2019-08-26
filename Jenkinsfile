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
                sh "xcodebuild \
                  -scheme JenkinsUnitTestTests\
                  -sdk iphonesimulator \
                  -destination 'platform=iOS Simulator,name=iPhone 8,OS=12.2' \
                  test "
            }
       }
    }
}