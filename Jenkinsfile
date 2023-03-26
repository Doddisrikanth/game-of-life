pipeline {
    agent any
    parameters {
        choice(name: 'MAVEN_GOAL', choices: ['compile', 'package'], description: 'MAVEN_GOAL')
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
                sh "mvn Choice: ${params.MAVEN_GOAL}" 
            }
        }
        stage('post build') {
            steps {
                archiveArtifacts artifacts: '**/target/gameoflife.war'
            }
        }
    }
}