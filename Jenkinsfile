pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'python -m py_compile C:\\EAI\\jenkinsDev\\simple-python-pyinstaller-app\\sources\add2vals.py C:\\EAI\jenkinsDev\\simple-python-pyinstaller-app\\sources\\calc.py'
            }
        }
        stage('Test') {
            steps {
                sh 'py.test --verbose --junit-xml test-reports/results.xml C:\\EAI\\jenkinsDev\\simple-python-pyinstaller-app\\sources\\test_calc.py'
            }
            post {
                always {
                    junit 'test-reports/results.xml'
                }
            }
        }
        stage('Deliver') {
            steps {
                sh 'pyinstaller --onefile C:\\EAI\\jenkinsDev\\simple-python-pyinstaller-app\\sources\\add2vals.py'
            }
            post {
                success {
                    archiveArtifacts 'dist/add2vals'
                }
            }
        }
    }
}
