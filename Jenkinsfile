pipeline {
 agent any
 tools {
   maven 'maven'
}
 stages {
  stage ('Initialize') {
   steps {
    sh '''
                echo "PATH = ${PATH}"
                echo "M2_HOME = ${M2_HOME}"   
        '''
      }
    }
  stage ('Build') {
   steps {
    sh 'mvn clean package'
  }
  }
  
  stage ('Deploy to Tomcat') {
   steps {
    sshagent (['tomcat']) {
     sh 'scp -o StrictHostKeyChecking=no target/*.war ubuntu@34.220.127.92:/home/ubuntu//prod/apache-tomcat-8.5.81/webapps/webapp.war'
     
          }
      }
  }
  
     
  }
}
