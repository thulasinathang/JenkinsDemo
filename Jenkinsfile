node{

   def tomcatWeb = '/Library/Tomcat/webapps'
   def tomcatBin = '/Library/Tomcat/bin'
   def tomcatStatus = ''
   stage('SCM Checkout'){
     git 'https://github.com/thulasinathang/JenkinsDemo.git'
   }
   stage('Compile-Package-create-war-file'){
      // Get maven home path
      def mvnHome =  tool name: 'Maven', type: 'maven'   
      sh "${mvnHome}/bin/mvn package"
      }
/*   stage ('Stop Tomcat Server') {
               bat ''' @ECHO OFF
               wmic process list brief | find /i "tomcat" > NUL
               IF ERRORLEVEL 1 (
                    echo  Stopped
               ) ELSE (
               echo running
                  "${tomcatBin}\\shutdown.bat"
                  sleep(time:10,unit:"SECONDS") 
               )
'''
   }*/
   stage('Deploy to Tomcat'){
     sh "cp target/JenkinsPipeline.war" ${tomcatWeb}""
   }
      stage ('Start Tomcat Server') {
         sleep(time:5,unit:"SECONDS") 
         sh "${tomcatBin}\\startup.sh"
         sleep(time:100,unit:"SECONDS")
   }
}
