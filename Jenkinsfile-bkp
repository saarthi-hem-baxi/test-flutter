pipeline {
    agent any

    environment {
        FLUTTER_HOME = "/home/saarthi/Android/flutter"
        APK_OUTPUT_DIR = "/home/saarthi/Android/flutter/apk" // Specify the output directory for APKs
        JAVA_ARGS = "-Xmx5g -XX:MaxPermSize=512m -Djava.awt.headless=true"
    }

    stages {
        stage('Checkout') {
            steps {
                timeout(time: 15, unit: 'MINUTES') {
                    checkout scm
                }
            }
        }

        stage('Build APK') {
            steps {
                timeout(time: 15, unit: 'MINUTES') {
                    script {
                        def flutterCmd = "${env.FLUTTER_HOME}/bin/flutter"
                        sh "java ${env.JAVA_ARGS} -jar ${flutterCmd} build apk --debug"
                    }
                }
            }
        }

        stage('Save APK') {
            steps {
                timeout(time: 15, unit: 'MINUTES') {
                    script {
                        sh "mkdir -p ${env.APK_OUTPUT_DIR}"
                        sh "cp build/app/outputs/flutter-apk/app-debug.apk ${env.APK_OUTPUT_DIR}/app-debug-${currentBuild.number}.apk"
                    }
                }
            }
        }

        stage('Run Tests') {
            steps {
                timeout(time: 15, unit: 'MINUTES') {
                    script {
                        def flutterCmd = "${env.FLUTTER_HOME}/bin/flutter"
                        sh "java ${env.JAVA_ARGS} -jar ${flutterCmd} test"
                    }
                }
            }
        }

        stage('TEST') {
            steps {
                timeout(time: 15, unit: 'MINUTES') {
                    sh "java ${env.JAVA_ARGS} -jar flutter test"
                }
            }
        }

        stage('BUILD') {
            steps {
                timeout(time: 15, unit: 'MINUTES') {
                    sh """
                      #!/bin/sh
                      java ${env.JAVA_ARGS} -jar flutter build apk --debug
                    """
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

