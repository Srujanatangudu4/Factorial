pipeline {
    agent any

    stages {
        stage('Compile') {
            steps {
                bat 'javac Factorial.java TestFactorial.java'
            }
        }
        stage('Test') {
            steps {
                bat 'java TestFactorial'
            }
        }
        stage('Run') {
            steps {
                bat 'java Factorial'
            }
        }
        stage('Package JAR') {
            steps {
                bat 'jar cfm Factorial.jar Manifest.txt Factorial.class TestFactorial.class'
            }
        }
        stage('Archive JAR') {
            steps {
                archiveArtifacts artifacts: 'Factorial.jar'
            }
        }
    }

    post {
        success {
            echo 'Build, test, run, and JAR creation successful and artifact is ready!'
        }
        failure {
            echo 'Build or test failed'
        }
    }
}
