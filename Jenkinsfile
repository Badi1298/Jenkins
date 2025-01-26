pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                cleanWs()
                echo 'Building a new laptop..'
                sh '''
                    mkdir -p build
                    echo "Mainboard" >> build/computer.txt
                    cat build/computer.txt
                    echo "Display" >> build/computer.txt
                    cat build/computer.txt
                    echo "Keyboard" >> build/computer.txt
                    cat build/computer.txt
                '''
            }
        }

        stage('Test') {
            steps {
                echo 'Testing the laptop..'
                sh '''
                    test -f build/computer.txt
                    grep -q Mainboard build/computer.txt
                    grep -q Display build/computer.txt
                    grep -q Keyboard build/computer.txt
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
