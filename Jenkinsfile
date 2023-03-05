node('AGENT'){
    stage('VCS'){
        git url: 'https://github.com/abhish0916dev/game-of-life.git',
            branch: 'scripted'
    }
    stage('Build the code'){
        sh 'mvn package'
    }
    stage('Archive Artifact'){
        archiveArtifacts artifacts: '**/target/gameoflife.war',
                        onlyIfSuccessful: true
    }
        
}