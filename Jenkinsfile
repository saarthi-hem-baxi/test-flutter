pipeline {
    agent any

    environment {
        FLUTTER_HOME = "/home/saarthi/Android/flutter"
        APK_OUTPUT_DIR = "/home/saarthi/Android/flutter/apk" // Specify the output directory for APKs
    }

    stages {
        stage('Set Diagnostics') {
            steps {
                script {
                    System.setProperty("org.jenkinsci.plugins.durabletask.BourneShellScript.LAUNCH_DIAGNOSTICS", "true")
                }
            }
        }

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build APK') {
            steps {
                script {
                    def flutterCmd = "${env.FLUTTER_HOME}/bin/flutter"
                    sh "${flutterCmd} --version" // Check Flutter version to verify Flutter setup
                    sh "${flutterCmd} build apk --debug"
                }
            }
        }

        stage('Save APK') {
            steps {
                script {
                    sh "mkdir -p ${env.APK_OUTPUT_DIR}" // Create the output directory if it doesn't exist
                    sh "cp build/app/outputs/flutter-apk/app-debug.apk ${env.APK_OUTPUT_DIR}/app-debug-${currentBuild.number}.apk"
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
            archiveArtifacts artifacts: "${env.APK_OUTPUT_DIR}/*.apk", allowEmptyArchive: true
        }
    }
}

