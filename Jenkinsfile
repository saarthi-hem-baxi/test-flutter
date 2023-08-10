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

//                     // Use sudo for the flutter build apk command
//                     sh "sudo flutter build apk --release --output=$apkOutputPath"
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

                    // Define the flutter build command
                    def flutterBuildCommand = "flutter build apk --release --output=$apkOutputPath"

                    // Use sudo to run the flutter build command
                    sh "sudo sh -c '${flutterBuildCommand}'"
                }
            }
        }
    }
}
