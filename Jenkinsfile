node('linux') 
    {   stage('Unit Tests') 
        {
            git 'https://github.com/amil3447/java-project.git' 
                sh 'ant -f test.xml -v'
                junit 'reports/result.xml'
            
        }   
        stage('Build') 
        {    
            sh 'ant -f build.xml -v'       
        }
        stage('Deploy')
        {
            sh 'aws s3 cp /workspace/java-pipeline/dist/*.jar s3://amil3447-assignment10/'
        }
		    stage('Report') 
        {
		        withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: '6e81b448-6ee8-4ac3-bf64-7a2216cc301c', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]) 
              {
						    // some block
						    sh 'aws cloudformation describe-stack-resources --region us-east-1 --stack-name jenkins'
				      }
		    }		
    }
