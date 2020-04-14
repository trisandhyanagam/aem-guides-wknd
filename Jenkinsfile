pipeline {
  agent any
   tools { 
        maven 'maven 3.6' 
        jdk 'JAVA_HOME' 
    }
  stages {
    stage('Build/NexusDeploy') {
      steps {
        script {
        	mvn deploy
        	echo 'This is jenkins job'
			sh '''mvn deploy'''
        }
      }
    }
    stage('Deploy to instance') {
      steps {
        input 'Deploy to instance ?'
        script {
            sh '''
            rm -rf aem-guides-wknd.ui.apps*
            wget --content-disposition "http://localhost:8081/service/rest/v1/search/assets/download?sort=version&repository=maven-snapshots&group=com.adobe.aem.guides&name=aem-guides-wknd.ui.apps&maven.extension=zip"
      	cp aem-guides-wknd.ui.apps* aem-guides-wknd.ui.apps.zip
curl -u "admin":"admin" --fail -F file=@"aem-guides-wknd.ui.apps.zip" -F force=true -F install=true 'http://localhost:4508/crx/packmgr/service.jsp'
'''
          }
        }

      }
    }
  }
