pipeline {
    agent {jenkins-agent}

    tools {
        maven 'mvn'
        jdk 'jdk'
    }

    stages {
        stage('Cloning Git') {
            steps {
                git branch: 'main',
                credentialsId: '1',
                url: 'https://github.com/zeynepkazu/jenkins-test.git'
            }
        }

        stage('Run Test') {
            steps {
                sh 'mvn clean install'
                sh 'mvn clean test'
            }
        }
    }

    post {
        always {
            allure includeProperties: false,
            jdk: 'jdk',
            results: [[path: 'target/allure-results']]
        }
    }
}
