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
        stage('BUILD') {
            steps {
                script {
                    // Define the output APK path
                    def apkOutputPath = "${env.APK_OUTPUT_DIR}/app-release.apk"

                    // Build the release APK and move it to the specified output directory
                    sh "flutter build apk --release --output=$apkOutputPath"
                }
            }
        }

        stage('Additional Steps') {
            steps {
                script {
                    // Navigate to the workspace directory
                    dir("/var/lib/jenkins/workspace/test-flutter") {
                        // Build the release APK using the provided command
                        sh "sudo flutter build apk --release"
                    }
                }
            }
        }
    }
}
