pipeline{
	tools{jdk 'JAVA_HOME'
			maven 'M2_HOME'
	
	}
	agent any
	stages
	{
			stage('checkout')
				{
					steps{
						git 'https://github.com/nafishaparween/jenkins_tomcat_deploy_warFile.git'
						}
				}
		stage('Clean') {
            steps {
                sh 'mvn clean'
            }
        }
			stage('compile')
			{
				steps{
						sh 'mvn compile'
				}
			}
			stage('test')
			{
				steps{
						sh 'mvn test'
				}
			}
    stage('package')
			{
				steps
        {
						sh 'mvn package'
				}
			}
   stage('install')
			{
				steps
        {
						sh 'mvn install'
				}
			}
    stage('deploy'){
    steps{
      echo "start deploy"
      scp -i "mykey.pem" *.war ec2-user@172.31.5.85:/home/ec2-user/tomcat10/webapps/
      echo "over "

    }
    }
			}
}
