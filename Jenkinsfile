pipeline {
    agent any

    parameters {
         string(name: 'tomcat_dev', defaultValue: '35.166.210.154', description: 'Staging Server')
         string(name: 'tomcat_prod', defaultValue: '34.209.233.6', description: 'Production Server')
    }

    triggers {
         pollSCM('* * * * *')
     }

stages{
        stage('Build'){
            steps {
                sh 'mvn clean package'
            }
            post {
                success {
                    echo 'Now Archiving...'
                   // archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }

        stage ('Deployments'){
            parallel{
                stage ('Deploy to Staging'){
                    steps {
                       // sh "cp -r /home/jenkins/tomcat-demo.pem **/target/*.war /home/deploy"
                        sh "ls"
                    }
                }

                stage ("Deploy to Production"){
                    steps {
                       def myapp = new SwingBuilder()
                        def buttonPanel = {
                                    myapp.panel(constraints : BorderLayout.SOUTH) {
	
                                        button(text : 'Option A', actionPerformed : {
                                         println 'accecpt'
                                 })
                     }
                    }
                        
                        //sh "cp -r /home/jenkins/tomcat-demo.pem **/target/*.war /home/webapps"
                        sh "date"
                    }
                }
            }
        }
    }
}
