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
            mail bcc: '', body: "BUILD URL: ${BUILD_URL} TEST RESULTS ${RUN_TESTS_DISPLAY_URL} ", cc: '', from: 'devops@qtdevops.com', replyTo: '', 
                subject: "${JOB_BASE_NAME}: Build ${BUILD_ID} Succeded", to: 'gannapuramashish1996@gmail.com'

        }
        failure{
            echo "failure"
            mail bcc: '', body: "BUILD URL: ${BUILD_URL} TEST RESULTS ${RUN_TESTS_DISPLAY_URL} ", cc: '', from: 'devops@qtdevops.com', replyTo: '', 
                subject: "${JOB_BASE_NAME}: Build ${BUILD_ID} failed", to: 'gannapuramashish1996@gmail.com'
        }
        }
    }

}
