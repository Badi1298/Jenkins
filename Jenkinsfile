pipeline {
    agent any

    environment {
        BUILD_FILE_NAME = 'laptop.txt'
    }

    stages {
        stage('Build') {
            steps {
                cleanWs()
                echo 'Building a new laptop..'
                sh '''
                    mkdir -p build
                    echo "Mainboard" >> build/$BUILD_FILE_NAME
                    cat build/$BUILD_FILE_NAME
                    echo "Display" >> build/$BUILD_FILE_NAME  
                    cat build/$BUILD_FILE_NAME
                    echo "Keyboard" >> build/$BUILD_FILE_NAME 
                    cat build/$BUILD_FILE_NAME
                '''
            }
        }

        stage('Test') {
            steps {
                echo 'Testing the laptop..'
                sh '''
                    test -f build/$BUILD_FILE_NAME
                    grep -q Mainboard build/$BUILD_FILE_NAME  
                    grep -q Display build/$BUILD_FILE_NAME
                    grep -q Keyboard build/$BUILD_FILE_NAME
                '''
            }
        }
    }

    post {
        success {
            archiveArtifacts artifacts: 'build/**'
        }
    }
}
