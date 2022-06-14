node('built-in')
{
    stage('Continues_Download')
   {
        git 'https://github.com/intelliqittrainings/maven.git'
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
        git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
        sh 'java -jar /var/lib/jenkins/workspace/ScriptedPipeline/testing.jar'
   }
    stage('Continues_Delivery')
   {
       input id: 'Kool', message: 'Need approval from the delivery manager'
        deploy adapters: [tomcat9(credentialsId: '533f109c-3aa7-4c8d-b888-2ffff107de95', path: '', url: 'http://172.31.10.108:8080')], contextPath: 'prodapp', war: '**/*.war'
   }
}

