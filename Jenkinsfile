pipeline {
    agent any
    environment {
        DB_URL = 'jdbc:mysql://54.198.190.17:3306/naruto1'
        DB_USER = 'naruto1'
        DB_PASS = '12345678NARUto'
        LIQUIBASE_HOME = '/usr/local/liquibase'  // Update path if different
    }
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
                    sh '${LIQUIBASE_HOME} --version'
                    // Run Liquibase update command
                    sh "${LIQUIBASE_HOME} --url=${DB_URL} --username=${DB_USER} --password=${DB_PASS} --changeLogFile=db/changelog.xml update"
                }
            }
        }
    }
}
