pipeline {
    agent {
        label "maven"
    }
    tools {
        jdk 'Openjdk8'
        maven 'Maven363'
    }
    stages {
        stage ('Build') {
            steps {
                sh "mvn clean test"
            }
        }
    }
    post {
        success {
            echo "good job"
        }
        failure {
            echo "Improve the skills"
        }
        always{
            echo "work hard"
        }
    }

}