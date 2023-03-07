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
            tools{
                jdk 'JDK_8'
            }
            steps{
                sh  'mvn package'
            }
        }
        // stage('copy build'){
        //     steps{
        //         sh 'mkdir -p /tmp/${JOB_NAME}/${BUILD_ID} && cp ./gameoflife-web/target/gameoflife.war /tmp/${JOB_NAME}/${BUILD_ID}/'
        //     }

        // }
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
    post{
        success{
            mail subject: "Jenkins jobs of ${JOB_NAME} of with ${BUILD_ID} is successfull",
                 body: "Please use this url ${BUILD_URL} for more information",
                 to: 'abhishek16tiwary@gmail.com',
                 from: 'jenkins@abhish.com'
        }
        failure{
            mail subject: "Jenkins jobs of ${JOB_NAME} of with ${BUILD_ID} is Failed",
                 body: "Please use this url {$BUILD_URL} for more information",
                 to: '${GIT_AUTHOR_EMAIL}',
                 from: 'jenkins@abhish.com'
        }
    }
}


