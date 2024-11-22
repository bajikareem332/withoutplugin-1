pipeline
{
    agent any
    stages
    {
         stage('clean workspace')
        {
          steps
          {
              cleanWs()
          } 
        }
        stage('download')
        {
          steps
          {
              git 'https://github.com/sudarshansw7/mymaven.git'
          } 
        }
        stage('build')
        {
            steps
            {
                sh 'mvn package'
            }
        }
        stage('deploy')
        {
            steps
            {
               sh 'scp /var/lib/jenkins/workspace/withoutplugin-1/webapp/target/webapp.war ubuntu@172.31.17.145:/var/lib/tomcat10/webapps/newapp.war'
            }
        }
        stage('testing')
        {
            steps
            {
                git 'https://github.com/sudarshansw7/myfunctionaltesting.git'
                sh 'java -jar /var/lib/jenkins/workspace/withoutplugin-1/testing.jar'
                
            }
        }
        stage('delivery')
        {
            steps
            {
                sh ' scp /var/lib/jenkins/workspace/withoutplugin-1/webapp/target/webapp.war ubuntu@172.31.16.220:/var/lib/tomcat10/webapps/prodapp.war'


            }
        }
        
        
    }
}
