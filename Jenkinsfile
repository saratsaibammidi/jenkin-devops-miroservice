pipeline {
    // Use this if you're running inside a Docker agent with preinstalled tools
    // agent {
    //     docker {
    //         image 'maven:3.9.9-eclipse-temurin-17' // Includes Java + Maven
    //         args '-v /var/run/docker.sock:/var/run/docker.sock'
    //     }
    // }
    
    agent any

    environment {
        dockerHome = tool 'myDocker'
        mavenHome = tool 'myMaven'
        PATH = "${dockerHome}/bin:${mavenHome}/bin:${env.PATH}"
    }

    stages {
        stage('Build Info') {
            steps {
                sh 'mvn --version'
                sh 'docker version'
                echo "BUILD"
                echo "PATH - $PATH"
                echo "BUILD_NUMBER - $env.BUILD_NUMBER"
                echo "BUILD_ID - $env.BUILD_ID"
                echo "JOB_NAME - $env.JOB_NAME"
                echo "BUILD_TAG - $env.BUILD_TAG"
                echo "BUILD_URL - $env.BUILD_URL"
            }
        }

        stage('Compile') {
            steps {
                sh 'mvn clean compile'
            }
        }

        stage('Unit Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Integration Test') {
            steps {
                // Ensure you have failsafe plugin configured in your pom.xml
                sh 'mvn failsafe:integration-test failsafe:verify'
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
