pipeline
{
    agent any
    stages
    {
        stage('ContinuousDownload_Master')
        {
            steps
            {
                git 'https://github.com/intelliqittrainings/maven.git'
            }
        }
        stage('ContinuousBuild_Master')
        {
            steps
            {
               sh label: '', script: 'mvn package'
            }
        }
        stage('ContinuousDeployment_Master')
        {
            steps
            {
               sh label: '', script: '''
scp /home/ubuntu/.jenkins/workspace/DeclarativePipeline/webapp/target/webapp.war ubuntu@172.31.45.245:/var/lib/tomcat8/webapps/newtestapp.war'''
            }
        }
        stage('ContinuousTesting_Master')
        {
            steps
            {
                git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
                sh label: '', script: 'java -jar /home/ubuntu/.jenkins/workspace/DeclarativePipeline/testing.jar'
            }
        }
        stage('ContinuousDelivery_Master')
        {
            steps
            {
                
                 sh label: '', script: '''
scp /home/ubuntu/.jenkins/workspace/DeclarativePipeline/webapp/target/webapp.war ubuntu@172.31.42.87:/var/lib/tomcat8/webapps/newprodapp.war'''
            }
        }
    }
}
