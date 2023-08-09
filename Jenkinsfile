pipeline {
    agent any

    environment {
        APK_OUTPUT_DIR = "/home/saarthi/Android/flutter/apk"
    }

    stages {
        stage('BUILD') {
            steps {
                script {
                    // Set the HEARTBEAT_CHECK_INTERVAL property
                    System.setProperty("org.jenkinsci.plugins.durabletask.BourneShellScript.HEARTBEAT_CHECK_INTERVAL", "3800")
                    
                    // Define the output APK path
                    def apkOutputPath = "${env.APK_OUTPUT_DIR}/app-release.apk"

                    // Build the release APK and move it to the specified output directory
                    sh "flutter build apk --release --output=$apkOutputPath"
                }
            }
        }
    }
}

