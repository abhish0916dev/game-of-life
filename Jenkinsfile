pipeline{
    agent{label 'AGENT'}
    stages{
        stage('VCS'){
            steps{
                git url: 'https://github.com/abhish0916dev/game-of-life.git',
                branch: 'declarative'
            }
        }
        stage('Build'){
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