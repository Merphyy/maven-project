pipeline {
    agent any
    tools{
        maven 'local maven'
    }
    stages{
        

        stage('Deploy to staging'){
            steps{
                build job:'deploy-to-staging'
            }
        }
    }
}
