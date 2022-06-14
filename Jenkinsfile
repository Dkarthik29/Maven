node('built-in')
{
    stage('Continues_Download')
   {
        git 'https://github.com/Dkarthik29/Maven.git'
   }
    stage('Continues_Build')
   {
         sh 'mvn package'
   }
       stage('Continues_Deployement')
   {
     deploy adapters: [tomcat9(credentialsId: '533f109c-3aa7-4c8d-b888-2ffff107de95', path: '', url: 'http://172.31.14.89:8080')], contextPath: 'testapp', war: '**/*.war'
   }
     stage('Continues_Testing')
   {
       git 'https://github.com/Dkarthik29/Testing.git'
        sh 'java -jar /var/lib/jenkins/workspace/ScriptedPipeline/testing.jar'
   }
    stage('Continues_Delivery')
   {
       
        deploy adapters: [tomcat9(credentialsId: '533f109c-3aa7-4c8d-b888-2ffff107de95', path: '', url: 'http://172.31.10.108:8080')], contextPath: 'prodapp', war: '**/*.war'
   }
}

