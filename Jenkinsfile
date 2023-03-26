pipeline {
    agent any
    parameters {
        string(name: 'MAVEN_GOAL', defaultValue: 'package', description: 'Maven Goal')
    }
    stages {
        stage('vcs') {
            steps {
                git url: 'https://github.com/khajadevopsmarch23/game-of-life.git',
                    branch: 'sri'
            }
        }
        stage('package') {
            steps {
                sh 'export PATH="/usr/lib/jvm/java-1.8.0-openjdk-amd64/bin:$PATH"'
            }
            steps {
                sh "mvn ${params.MAVEN_GOAL}"
            }
        }
        stage('post build') {
            steps {
                archiveArtifacts artifacts: '**/target/gameoflife.war'
            }
        }
    }
}