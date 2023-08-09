pipeline {
    agent any

    environment {
         APK_OUTPUT_DIR = "/home/saarthi/Android/flutter/apk"
    }

    stages {
        stage('Build Release APK') {
            steps {
                script {
                    // Define the output APK path within the script block
                    def apkOutputPath = "${env.APK_OUTPUT_DIR}/app-release.apk"

                    // Execute the Flutter build command using Shell script
                    sh """
                    flutter build apk --release --output=$apkOutputPath
                    """
                }
            }
        }
    }
}

