pipeline {
    agent any

    environment {
        DIRECTORY_PATH = "/Users/liiiii/Desktop/SIT753PPIT/week8 "
        TESTING_ENVIRONMENT = "Test_Environment"
        PRODUCTION_ENVIRONMENT = "Yixuan_Li"
    }

    stages {
        stage('Build') {
            steps {
                echo "Fetch the source code from the directory path specified by the environment variable: ${env.DIRECTORY_PATH}"
                echo "Compile the code and generate any necessary artefacts"
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo "Unit tests"
                echo "Integration tests"
            }
        }

        stage('Code Analysis') {
            steps {
                echo "Integrate a code analysis tool to analyse the code"
            }
        }

        stage('Security Scan') {
            steps {
                echo "identify any vulnerabilities"
            }
        }

         stage('Deploy to Staging') {
            steps {
                echo "Deploy the application to a staging server"
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo "Run integration tests on the staging server"
            }
        }


        stage('Deploy to Production') {
            steps {
                echo "Deploying the code to the production environment: ${env.PRODUCTION_ENVIRONMENT}"
            }
        }
    }
}
