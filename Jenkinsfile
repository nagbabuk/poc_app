node {
      stage('SCM Checkout'){      
      git 'https://github.com/nagbabuk/poc_app'
      }
      stage('Compile-Package'){
            //getting ant path         
           def antHome = tool name: 'ant', type: 'ant'
           env.JAVA_HOME = tool name: 'java', type: 'jdk'
           sh "${antHome}/bin/ant war"
      }
      stage('Deploy-tomcat'){
       sshagent(['test-ubuntu']) {
    // some block
             sh 'scp -o StrictHostKeyChecking=no /var/lib/jenkins/workspace/test/dist/lib/*.war root@192.168.33.12:/opt/tomcat/webapps'
       }     
      }


}
