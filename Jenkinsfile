import groovy.swing.SwingBuilder 
import javax.swing.* 
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
                       class MyModel {
 			  @Bindable int count = 0
				}

			def model = new MyModel()
			new SwingBuilder().edt {
  			frame(title: '', size: [100, 100], locationRelativeTo: null, show: true) {
   			 gridLayout(cols: 1, rows: 2)
    			 label(text: bind(source: model, sourceProperty: 'count', converter: { v ->  v? "Clicked $v times": ''}))
   			 button('Click me!', actionPerformed: { model.count++ })
  

                    
                        
                        //sh "cp -r /home/jenkins/tomcat-demo.pem **/target/*.war /home/webapps"
                        sh "date"
                    }
                }
            }
        }
    }
}
