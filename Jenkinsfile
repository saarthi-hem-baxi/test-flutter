pipeline {
    agent any

    environment {
        FLUTTER_HOME = "/home/saarthi/Android/flutter"
        APK_OUTPUT_DIR = "/home/saarthi/Android/flutter/apk"
    }

    stages {
        stage('SETUP FLUTTER') {
            steps {
                sh "${env.FLUTTER_HOME}/bin/flutter doctor"
            }
        }

        stage('TEST') {
            steps {
                sh "${env.FLUTTER_HOME}/bin/flutter test"
            }
        }

        stage('BUILD') {
            steps {
                script {
                    // Define the output APK path
                    def apkOutputPath = "${env.APK_OUTPUT_DIR}/app-debug.apk"

                    // Build the APK
                    sh "${env.FLUTTER_HOME}/bin/flutter build apk --debug --output=$apkOutputPath"
                }
            }
        }
    }
}

