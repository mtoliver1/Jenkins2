pipeline {
    agent any

    tools {
        // Install the Maven version configured as "M3" and add it to the path.
        maven "3.9.9"
    }

    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/mtoliver1/Jenkins.git'
            }
        }
        stage('Build') {
            steps {
                bat 'mvn -Dmaven.test.failure.ignore=true clean package'
            }
        }
    }

    post {
        success {
            junit '**/target/surefire-reports/TEST-*.xml'
            archiveArtifacts 'target/*.jar'
        }
    }
}
