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