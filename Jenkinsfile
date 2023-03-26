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
            tools {
                jdk 'JAVA_8'
            }
            steps {
                sh 'mvn package'
            }
        }
        stage('post build') {
            steps {
                archiveArtifacts artifacts: '**/target/gameoflife.war'
            }
        }
    }
}