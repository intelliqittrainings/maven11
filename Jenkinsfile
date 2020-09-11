pipeline
{
    agent any
    stages
    {
        stage('ContinuousDownload_Loans')
        {
            steps
            {
                git 'https://github.com/intelliqittrainings/maven.git'
            }
        }
        stage('ContinuousBuild_Loans')
        {
            steps
            {
               sh label: '', script: 'mvn package'
            }
        }
}

	}
