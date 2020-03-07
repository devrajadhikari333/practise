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
                sh "mvn clean test surefire-report:report-only"
                publishHTML([allowMissing: true, alwaysLinkToLastBuild: false, keepAll: false, reportDir: 'target/site', reportFiles: 'surefire-report.html', reportName: 'TestReport', reportTitles: ''])
            }
        }
        stage ('Packaging') {
            steps {
                sh "mvn package -DskipTests=true"
            }
        }
        stage ('Deploy') {
            steps {
                sshagent(['agent-practise-key']) {
                sh "scp target/my-app-1.0-SNAPSHOT.jar ec2-user@172.31.38.40:/home/ec2-user" 
                }
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