// node('JDK8'){
//     stage('sourcecode'){
//         git branch: 'develop', url: 'https://github.com/ashishdevops123/gameoflife.git'
//     }
//     stage('build the code'){
//         sh 'mvn clean package'
//     }
//     stage('junit and archieve'){
//         junit '**/surefire-reports/*.xml'
//         archiveArtifacts artifacts: '**/target/*.war', followSymlinks: false
//     }
// }



pipeline{
    agent{ label'JDK8'}
    options{
        timeout(time: 1, unit: 'HOURS')
        retry(3)
        }
    triggers{
        cron('0 * * * *')
    }
    stages{
        stage('sourcecode'){
            steps{
                git url: 'https://github.com/ashishdevops123/gameoflife.git'
                
            }
        }
        stage('build'){
            steps{
                sh script: 'mvn clean package'
            }
        }
        stage('junit and archieve'){
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
