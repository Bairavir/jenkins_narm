pipeline {
    agent any
    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/Bairavir/jenkins_narm.git'
            }
        }
        stage('Apply SQL Changes') {
            steps {
                script {
                    // Ensure liquibase command is available
                    sh 'liquibase --version'
                    // Run Liquibase update command
                    sh 'liquibase --changeLogFile=db/changelog.xml update'
                }
            }
        }
    }
}
