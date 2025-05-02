pipeline {
    agent any
    environment {
        dockerHome = tool 'myDocker'
        mavenHome = tool 'myMaven'
        PATH = "${dockerHome}/bin:${mavenHome}/bin:${env.PATH}"
    }
    stages {
        stage('Build') {
            steps {
                sh 'mvn --version'
                sh 'docker version'
                echo "Build"
                echo "PATH -$PATH"
                echo "BUILD_NUMBER - $env.BUILD_NUMBER"
                echo "BUILD_ID - $env.BUILD_ID"
                echo "JOB_NAME - $env.JOB_NAME"
                echo "BUILD_TAG - $env.BUILD_TAG"
                echo "BUILD_URL -$env.BUILD_URL"
            }
        }

        stage('Compile') {
            steps {
                sh "mvn clean compile"
            }
        }

        stage('Integration test') {
            steps {
                sh "mvn failsafe:integration-test failsafe:verify" // Fixed typo
            }
        }

        stage('Test') {
            steps {
                sh "mvn test"
            }
        }
    }
    post {
        always {
            echo 'This will run after every pipeline run.'
        }
        success {
            echo 'This will run only if the pipeline was successful.'
        }
        failure {
            echo 'This will run only if the pipeline failed.'
        }
    }
}
