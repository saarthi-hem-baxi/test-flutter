pipeline {
    agent any

    environment {
        APK_OUTPUT_DIR = '/path/to/output/directory'
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
                    
                    // Check if build error occurred (this is just a placeholder)
                    if (/* your condition to check build error */) {
                        build_error = true
                    }

                    // Print a message if tests failed
                    if (build_error) {
                        echo "TESTS FAILED!"
                    }
                }
            }
        }
    }
}

