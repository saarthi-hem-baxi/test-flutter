pipeline {
    agent any

    environment {
        FLUTTER_HOME = "/home/saarthi/Android/flutter" // Set the path to your Flutter installation
        APK_OUTPUT_PATH = "/home/saarthi/Android/flutter/apk/app-debug.apk" // Set the desired output path for the APK
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build APK') {
            steps {
                script {
                    def flutterCmd = "${env.FLUTTER_HOME}/bin/flutter"
                    sh "${flutterCmd} build apk --debug"
                }
            }
        }

        stage('Save APK') {
            steps {
                script {
                    sh "cp build/app/outputs/flutter-apk/app-debug.apk ${env.APK_OUTPUT_PATH}"
                }
            }
        }

        stage('Run Tests') {
            steps {
                script {
                    def flutterCmd = "${env.FLUTTER_HOME}/bin/flutter"
                    sh "${flutterCmd} test"
                }
            }
        }
    }

    post {
        always {
            archiveArtifacts artifacts: 'build/app/outputs/flutter-apk/*.apk', allowEmptyArchive: true
        }
    }
}

