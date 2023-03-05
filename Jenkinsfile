node('AGENT'){
    stage('VCS'){
        git url: 'https://github.com/abhish0916dev/game-of-life.git',
            branch: 'scripted'
    }
    stage('Build the code'){
        sh 'PATH="usr/lib/jvm/java-1.8.0-openjdk-amd64/bin:$PATH" && mvn package'
    }
    stage('Archive Artifact'){
        archiveArtifacts artifacts: '**/target/gameoflife.war',
                        onlyIfSuccessful: true
    }
        
}