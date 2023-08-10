// pipeline {
//     agent any

//     environment {
//         APK_OUTPUT_DIR = "/home/saarthi/Android/flutter/apk"
//     }

//     stages {
//         stage('BUILD') {
//             steps {
//                 script {
//                     // Define the output APK path
//                     def apkOutputPath = "${env.APK_OUTPUT_DIR}/app-release.apk"

//                     // Build the release APK and move it to the specified output directory
//                     sh "flutter build apk --release --output=$apkOutputPath"
//                 }
//             }
//         }
//     }
// }
pipeline {
    agent any

    environment {
        APK_OUTPUT_DIR = "/home/saarthi/Android/flutter/apk"
    }

    stages {
        stage('Setup Environment') {
            steps {
                script {
                    // Set up Flutter environment
                    sh "sudo flutter doctor -v"
                    sh "sudo flutter config --no-analytics"
                }
            }
        }

        stage('BUILD') {
            steps {
                script {
                    // Define the output APK path
                    def apkOutputPath = "${env.APK_OUTPUT_DIR}/app-release.apk"

                    // Build the release APK and move it to the specified output directory
                    sh "sudo flutter build apk --release --output=$apkOutputPath"
                }
            }
        }
    }
}

