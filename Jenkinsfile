pipeline {
    agent any
    parameters {
        choice(name: 'MVN_GOAL', choices: ['compile', 'package'])
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
                sh 'export PATH="/usr/lib/jvm/java-1.8.0-openjdk-amd64/bin:$PATH", echo "Choice: ${params.MVN_GOAL}"'
                echo "Choice: ${params.MVN_GOAL}"
            }
        }
        stage('post build') {
            steps {
                archiveArtifacts artifacts: '**/target/gameoflife.war'
            }
        }
    }
}