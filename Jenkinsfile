pipeline{
    agent{ label'JDK8'}
    options{
        timeout(time: 1, unit: 'HOURS')
        retry(1)
        }
    triggers{
        cron('0 * * * *')   
    }
    stages{
        stage('sourcecode'){
            steps{
                git url: 'https://github.com/ashishdevops123/gameoflife.git',
                    branch: 'develop'
                
            }
        }
        stage('build'){
            steps{
                sh script: 'mvn clean package'
            }
        }
        stage('reporting'){
            steps{
                junit testResults: 'gameoflife-web/target/surefire-reports/*.xml'
               
            }
        }
    }
    post{
        success{
            echo "success"
            mail bcc: '', body: 'build passed ' "$BUILD_ID", cc: '', from: '', replyTo: '', subject: 'build url is "$BUILD_URL" , to: 'gannapuramashish1996@gmail.com'

        }
        failure{
            echo "failure"
        }
    }

}
