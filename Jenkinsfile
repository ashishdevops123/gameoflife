node('JDK8'){
    stage('sourcecode'){
        git branch: 'develop', url: 'https://github.com/ashishdevops123/gameoflife.git'
    }
    stage('build the code'){
        sh 'mvn clean package'
    }
    stage('junit and archieve'){
        junit '**/surefire-reports/*.xml'
        archiveArtifacts artifacts: '**/target/*.war', followSymlinks: false
    }
}