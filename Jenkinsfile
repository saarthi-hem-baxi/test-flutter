pipeline {
    agent any

    options {
        // Set the custom workspace directory
        workspace("/home/saarthi")
    }

    environment {
         APK_OUTPUT_DIR = "/home/saarthi/Android/flutter/apk"
    }

    stages {
        stage('Build Release APK') {
            steps {
                script {
                    // Define the output APK path within the script block
                    def apkOutputPath = "${env.APK_OUTPUT_DIR}/app-release.apk"
                    def build_error = false  // Initialize the build error flag

                    // Run the Flutter build command using Shell script
                    sh """
                    flutter build apk --release --output=$apkOutputPath
                    """
                    
                    // Check if build error occurred
                    if (currentBuild.resultIsWorseOrEqualTo('FAILURE')) {
                        build_error = true
                    }

                    // Print a message if build failed
                    if (build_error) {
                        echo "BUILD FAILED!"
                    }
                }
            }
        }
    }
}
