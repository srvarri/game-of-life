pipeline {
    agent { label 'jdk' }
    
    
    stages {
        stage('vcs') {
            steps {
                git branch: 'master', url:'https://github.com/srvarri/game-of-life.git'
            }

        }
        stage('build') {
            steps {
                sh '/usr/share/maven/bin/mvn package'
            }
        }

        stage('archive results') {
            steps {
                junit '**/surefire-reports/*.xml'
            }
        }
		stage ( 'artifacts') {
            steps {
                archiveArtifacts artifacts: '**/target/*.war'
            }
		}
    }    
}    