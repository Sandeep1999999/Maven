pipeline
{
  agent any
  stages
  {
      stage('cont download')
        {
            steps
            {
              git 'https://github.com/Sandeep1999999/Maven.git'  
            }
        } 
        stage('cont build')
        {
            steps
            {
                sh 'mvn package'
            }
        }      
       stage('cont deploy')
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: '8546d0ff-3e35-49da-8ec6-a7a42b9c16b4', path: '', url: 'http://172.31.0.117:8080')], contextPath: 'demoapp', war: '**/*.war'
            }
        }      
        stage('cont testing')
        {
            steps
            {
                git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
                sh 'java -jar /var/lib/jenkins/workspace/Declarativepipeline/testing.jar'
                
            }
        }      
        stage('cont delivery')
        {
            steps
            {
      
                deploy adapters: [tomcat9(credentialsId: '8546d0ff-3e35-49da-8ec6-a7a42b9c16b4', path: '', url: 'http://172.31.1.2:8080')], contextPath: 'prodapp', war: '**/*.war'
            }
        }
  }
    
    
    
    
}

    
    
    
