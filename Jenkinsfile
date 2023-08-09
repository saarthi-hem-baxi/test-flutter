pipeline {
    agent any

    stages {
        stage('Build Release APK') {
            environment {
                APK_OUTPUT_DIR = "/home/saarthi/Android/flutter/apk"
            }
            steps {
                script {
                    def apkOutputPath = "${env.APK_OUTPUT_DIR}/app-release.apk"
                    def flutterPath = "/home/saarthi/Android/flutter/bin"
                    def build_error = false

                    withEnv(["PATH=${flutterPath}:${env.PATH}"]) {
                        sh """
                        flutter build apk --release --output=$apkOutputPath
                        """
                    }
                    
                    if (currentBuild.resultIsWorseOrEqualTo('FAILURE')) {
                        build_error = true
                    }

                    if (build_error) {
                        echo "BUILD FAILED!"
                    }
                }
            }
        }
    }
}
