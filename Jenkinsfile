pipeline {
    agent any
    tools{
        maven 'local maven'
    }
    parameters{
        string(name: 'tomcat_dev', defaultValue: '3.128.172.143', description: 'Staging Server')
        string(name: 'tomcat_prod', defaultValue: '3.21.228.219', description: 'Production Server')
    }
    triggers {
         pollSCM('* * * * *')
     }
     stages{
     stage ('Deployments'){
            parallel{
                stage ('Deploy to Staging'){
                    steps {
                        sh "scp -i /Users/liuyang/Downloads/tomcat-demo.pem **/webapp/target/*.war ec2-user@${params.tomcat_dev}:/var/lib/tomcat8/webapps"
                    }
                }

                stage ("Deploy to Production"){
                    steps {
                        sh "scp -i /Users/liuyang/Downloads/tomcat-demo.pem **/webapp/target/*.war ec2-user@${params.tomcat_prod}:/var/lib/tomcat8/webapps"
                    }
                }
            }
        }
    }
}
