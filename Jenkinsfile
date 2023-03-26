pipeline {
    agent any
    parameters {
        string(name: 'MVN_GOAL', defaultValue: 'package')
    }
    triggers{
        pollSCM('* * * * *')
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
                sh 'export PATH="/usr/lib/jvm/java-1.8.0-openjdk-amd64/bin:$PATH", "mvn ${params.MAVEN_GOAL}"'
            }
        }
        stage('post build') {
            steps {
                archiveArtifacts artifacts: '**/target/gameoflife.war'
            }
        }
    }
}