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
