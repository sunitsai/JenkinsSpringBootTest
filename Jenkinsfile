pipeline {
    agent any

    tools {
        maven 'M3'
    }

    stages {
        stage('Clone Repo') {
            steps {
                git url: 'https://github.com/sunitsai/JenkinsSpringBootTest.git', branch: 'main'
            }
        }

        stage('Build App') {
            steps {
                sh 'mvn clean install'
            }
        }

        stage('Test API') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Run App') {
            steps {
                sh 'java -jar target/*.jar &'
                echo 'Spring Boot App Started!'
            }
        }
    }
}
