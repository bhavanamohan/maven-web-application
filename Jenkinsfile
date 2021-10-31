def mavenhome=tool name:'MavenExample',type:'maven' 
node()
{
stage('code from git')
  {
    git 'https://github.com/bhavanamohan/maven-web-application.git'
  }
  stage('maven package')
  {
    sh {mavenhome}/bin/mvn clean package
  }
  stage('sonarqube reports')
  {
    sh {mavenhome}/bin/mvn sonar:sonar
  }
  stage('store package in nexus')
  {
    sh {mavenhome}/bin/mvn deploy
  }
  stage('deploy to tomcat')
  {
    cp /var/lib/jenkins/workspace/Freestyle job example/target/maven-web-application.war /opt/apache-tomcat-9.0.54/webapps/maven-web-application.war
  }
  
}
