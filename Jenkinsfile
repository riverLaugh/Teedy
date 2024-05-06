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
        stage('pmd') {
                steps {
                sh 'mvn pmd:pmd'
            }
        }

    }

    post {
        always {
            archiveArtifacts artifacts: '**/target/site/**', fingerprint: true
            archiveArtifacts artifacts: '**/target/**/*.jar', fingerprint: true
            archiveArtifacts artifacts: '**/target/**/*.war', fingerprint: true
        }
    }

}
