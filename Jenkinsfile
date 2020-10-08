pipeline {
    agent any
    tools{
        maven 'local maven'
    }
    stages{
        stage('Build'){
            steps {
                sh 'mvn install'
            }
            post {
                success {
                    echo '开始存档***'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
    }
}
