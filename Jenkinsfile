//declarative pipeline for Game-of-life"
pipeline{
    agent{label 'AGENT'}
    // triggers {cron ('H/2 * * * *')}
    triggers{pollSCM('* * * * *')}
    stages{
        stage('VCS'){
            steps{
                git url: 'https://github.com/abhish0916dev/game-of-life.git',
                branch: 'declarative'
            }
        }
        stage('Build'){
            steps{
                sh 'export PATH="/usr/lib/jvm/java-1.8.0-openjdk-amd64/bin:$PATH" && mvn package'
            }
        }
        stage('Archieve Artifact'){
            steps{
                archiveArtifacts artifacts: '**/target/gameoflife.war',
                        onlyIfSuccessful: true
            }
        }
        stage('Publish Test Result'){
            steps{
                junit testResults: '**/surefire-reports/TEST-*.xml'
            }
        }
    }
}


