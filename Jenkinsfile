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

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build APK Release') {
            steps {
                script {
                    // Use a script block to handle multiple commands
                    sh 'sudo flutter build apk --release'
                }
            }
            post {
                always {
                    archiveArtifacts artifacts: 'build/app/outputs/flutter-apk/app-release.apk', allowEmptyArchive: true
                }
            }
        }
    }
}
