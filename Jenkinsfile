pipeline {
  agent any
  stages {
    stage('Deploy to instance') {
      steps {
        input 'Deploy to instance ?'
        script {
		 bat ''' 
		 del aem-guides-wknd.ui.apps.zip
		 wget --content-disposition "http://localhost:8081/service/rest/v1/search/assets/download?sort=version&repository=maven-snapshots&group=com.adobe.aem.guides&name=aem-guides-wknd.ui.apps&maven.extension=zip"
      	    copy aem-guides-wknd.ui.apps* aem-guides-wknd.ui.apps.zip
           curl -u "admin":"admin" --fail -F file="aem-guides-wknd.ui.apps.zip" -F force=true -F install=true 'http://localhost:4507/crx/packmgr/service.jsp'
'''
          
          }
        }

      }
    }
  }