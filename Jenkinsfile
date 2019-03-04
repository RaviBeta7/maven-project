//import groovy.swing.SwingBuilder 
//import javax.swing.* 
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

         stage ('Deployments'){
            parallel{
                stage ('Deploy to Staging'){
                    steps {
			   sh "ls"
                        //sh "scp -i /home/jenkins/tomcat-demo.pem **/target/*.war ec2-user@${params.tomcat_dev}:/var/lib/tomcat7/webapps"
                    }
                }

          stage ("Deploy to Production"){
                    steps {
			    sh "date"
                        //sh "scp -i /home/jenkins/tomcat-demo.pem **/target/*.war ec2-user@${params.tomcat_prod}:/var/lib/tomcat7/webapps"
                    }
	  	}
            }
        }
    }
}
