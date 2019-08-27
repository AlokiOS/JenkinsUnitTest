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
            steps {
            parallel (
                        "Unit Tests": {
                           sh "xcodebuild \
                  -scheme JenkinsUnitTestTests\
                  -sdk iphonesimulator \
                  -destination 'platform=iOS Simulator,name=iPhone 8,OS=12.2' \
                  test "
                        },
                        "UI Tests": {
                            sh "xcodebuild -project JenkinsUnitTest.xcodeproj -scheme "UITests" -sdk iphonesimulator -destination 'platform=iOS Simulator,name=iPhone 8,OS=12.2' test"
                        }
                    )
        }
            
       }
       stage('Archive'){
            steps{
               sh "mkdir -p build/build"
               sh "xcodebuild archive -project JenkinsUnitTest.xcodeproj -scheme JenkinsUnitTest -archivePath ~/builds/build/JenkinsUnitTest.xcarchive"
            }
       }
       stage('Ipa'){
            steps{
               sh "xcodebuild -exportArchive -archivePath ~/builds/build/JenkinsUnitTest.xcarchive -exportOptionsPlist exportOptions.plist -exportPath ~/builds/build"
            }
       }
    }
}