node('AGENT'){
    stage('VCS'){
        git url: 'https://github.com/abhish0916dev/game-of-life.git',
            branch: 'scripted'
    }
    stage('Build the code'){
        sh 'export PATH="/usr/lib/jvm/java-1.8.0-openjdk-amd64/bin:$PATH" && mvn package'
    }
    stage('Archive Artifact'){
        archiveArtifacts artifacts: '**/target/gameoflife.war',
                        onlyIfSuccessful: true
    }
    stage('Test Results'){
        junit testResults: '**/game-of-life-web/target/surefire-reports/TEST-*.xml'
    }
        
}