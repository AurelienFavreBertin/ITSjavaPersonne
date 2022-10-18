pipeline {
    agent any
    stages {
        stage('Clone') {
            steps {
                pwd
                sh ' rm -r * .*'
                git branch: 'main',
                    url: 'git@github.com:AurelienFavreBertin/ITSjavaPersonne.git'
                echo "repo git cloned!!"
            }
        }
        stage('Build') {
            steps {
                sh '''
                cd ITSjavaPersonne
                mvn clean
                mvn verify
                mvn compile
                mvn validate
                mvn package
                echo "App Built"
                '''
            }
        },
        stage('Run') {
            steps {
                sh '''
                cd ITSjavaPersonne
                mvn run
                echo "Running ${env.BUILD_ID} on ${env.JENKINS_URL}"
                '''
            }
        }
    }
}