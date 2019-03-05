node('maven-label') {
   def mvnHome
   stage('Preparation') { 
      git 'https://github.com/cicd-2/aib.git'       
      mvnHome = tool 'mavn-3.6.0'
   }
   stage('Build') {
     
      if (isUnix()) {
         sh "'${mvnHome}/bin/mvn' -Dmaven.test.failure.ignore clean package"
      } else {
         bat(/"${mvnHome}\bin\mvn" -Dmaven.test.failure.ignore clean package/)
      }
   }
   stage('Results') {
      junit '**/target/surefire-reports/TEST-*.xml'
      archiveArtifacts 'target/*.jar'
   }
}
