pipeline {
    agent {
        label 'SLAVE'
     }
    tools {
        maven 'M2_HOME'
    }
    stages {
        stage('checkout from project') {
            steps {
                git branch: 'main' , url: 'https://github.com/belosheabhijeet/java-maven-pipeline-jenkins.git'
            }
        }
        stage('Build the Package') {
            steps {
                sh 'mvn test'
            }
        }
        stage('Deploying') {
            steps {
                deploy adapters: [tomcat9(credentialsId: '4bb61774-e910-48da-bb90-b7355e399918', path: '', url: 'http://35.154.17.110:8081/manager/html')], contextPath: null, war: '**/*.war'
            }
        }
    }
}
