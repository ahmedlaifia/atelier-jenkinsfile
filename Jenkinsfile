pipeline {
    agent any
    // Alternatively, you can specify a specific agent like this:
    // agent {
    //     node {
    //         label 'build'
    //     }
    // }

    tools {
        maven 'M2_HOME'
    }

    options {
        // Timeout counter starts after agent is allocated
        timeout(time: 10, unit: 'MINUTES')
    }

    environment {
        APP_ENV = "DEV"
    }

    stages {
        stage('Code Checkout') {
            steps {
                git branch: 'main', 
                    url: 'https://github.com/ahmedlaifia/atelier-jenkinsfile.git'
            }
        }

        stage('Code Build') {
            steps {
               sh 'mvn clean package'
            }
        }
    }

    post {
        always {
            echo "======always======"
        }
        success {
            echo "=====pipeline executed successfully ====="
        }
        failure {
            echo "======pipeline execution failed======"
        }
    }
}
