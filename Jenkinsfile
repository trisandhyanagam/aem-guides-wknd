pipeline {
  agent any
  stages {
    stage('Deploy to instance') {
      steps {
        input 'Deploy to instance ?'
        script {
		 bat ''' 
      	    copy "ui.apps\target\aem-guides-wknd.ui.apps*" aem-guides-wknd.ui.apps.zip
           curl -u "admin":"admin" --fail -F file="aem-guides-wknd.ui.apps.zip" -F force=true -F install=true 'http://localhost:4507/crx/packmgr/service.jsp'
'''
          
          }
        }

      }
    }
  }