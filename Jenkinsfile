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
                junit testResults: 'target/surefire-reports/*.xml'
               
            }
        }
    }
    post{
        success{
            echo "success"

        }
        failure{
            echo "failure"
        }
    }

}
