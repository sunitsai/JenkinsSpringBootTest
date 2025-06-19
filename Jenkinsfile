pipeline {
    agent any

    tools {
        maven 'M3' // Make sure this matches the Maven installation name in Jenkins
        jdk 'JDK 17'        // Make sure this matches the JDK installation name in Jenkins
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/sunitsai/JenkinsSpringBootTest.git'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean package -DskipTests'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
            post {
                always {
                    junit '**/target/surefire-reports/*.xml'
                }
            }
        }
        stage('Run Spring Boot App') {
            steps {
                sh 'nohup mvn spring-boot:run &'
            }
        }
    }
    post {
        always {
            echo 'Pipeline completed.'
        }
    }
}
