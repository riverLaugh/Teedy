pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'mvn -B -DskipTests clean package' // Build project without tests
            }
        }
        stage('Unit Tests') {
            steps {
                sh 'mvn test' // Execute unit tests using Maven Surefire plugin
            }
        }
        stage('Javadoc Generation') {
            steps {
                sh 'mvn javadoc:javadoc' // Generate Javadoc using Maven Javadoc plugin
            }
        }
    }
    post {
        always {
            // Archive Surefire reports
            archiveArtifacts artifacts: '**/target/surefire-reports/**', fingerprint: true
            // Archive Javadoc artifacts
            archiveArtifacts artifacts: '**/target/site/apidocs/**', fingerprint: true
        }
    }
}
