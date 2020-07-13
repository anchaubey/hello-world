pipeline {
    agent any
    stages {
        stage('Git pull') {
            steps {
                git credentialsId: 'GITHUB_ID', url: 'https://github.com/anchaubey/hello-world.git'
            }
                   }
        stage('Build Application') {
            steps {
                sh 'mvn clean package'
            }
            post {
                success {
                    echo "Now Archiving the Artifacts...."
                    archiveArtifacts artifacts: '**/*.war'
                }
            }
        }
        stage('Create Tomcat Docker Image'){
            steps{
                sh 'docker build -t tomcatsamplewebapp:latest .'
            }            
        }
    }
}
