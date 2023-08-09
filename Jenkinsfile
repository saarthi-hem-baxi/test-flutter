pipeline {
    agent any

    environment {
        APK_OUTPUT_DIR = "/home/saarthi/Android/flutter/apk"
    }

    stages {
        stage('Build Release APK') {
            steps {
                script {
                    // Define the output APK path
                    def apkOutputPath = "${env.APK_OUTPUT_DIR}/app-release.apk"

                    // Build the release APK and move it to the specified output directory
                    sh "flutter build apk --release --output=\"$apkOutputPath\""
                }
            }
        }
    }

    post {
        always {
            echo "Release APK build completed."
        }
    }
}

script {
    System.setProperty("org.jenkinsci.plugins.durabletask.BourneShellScript.HEARTBEAT_CHECK_INTERVAL", "3800")
}

