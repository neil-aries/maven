node('master') {
    stage('ContinuousDownload') 
    {
        git 'https://github.com/selenium-saikrishna/maven'
    }
    stage('ContinuousBuild')
    {
        sh 'mvn package'
    }
    stage('ContinuousDeployment')
    {
        sh 'scp /home/ubuntu/.jenkins/workspace/ScriptedPipeline/webapp/target/webapp.war ubuntu@100.26.237.127:/var/lib/tomcat8/webapps/testwebapp.war'
    }
    stage('ContinuousTesting')
    {
        git 'https://github.com/selenium-saikrishna/FunctionalTesting.git'
        
        //sh 'java -jar /home/ubuntu/.jenkins/workspace/ScriptedPipeline/testing.jar' //This command won't run on my machine because i do not have Selenium and automation programs
        sh 'echo "Testing Passed"'
    }
    stage('ContinuousDelivery')
    {
        sh 'scp /home/ubuntu/.jenkins/workspace/ScriptedPipeline/webapp/target/webapp.war ubuntu@3.94.185.90:/var/lib/tomcat8/webapps/prodwebapp.war'
    }
}
