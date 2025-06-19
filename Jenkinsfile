pipeline {
    agent any

    tools {
        maven 'M3' 
    }

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/sunitsai/JenkinsSpringBootTest.git', branch: 'main'
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
