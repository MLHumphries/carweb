node('ubuntu-appServer-conTest')
{
	def app
	stage('Cloning Git')
	{
		//Checks for repo
		checkout scm
	}

	stage('Build-and-Tag')
	{
		//Builds image. Same as docker build on command line
		app.docker.build('mlhumphries/carweb')
	}

	stage('Post-to-DockerHub')
	{
		//
		docker.withRegistry('https://registry.hub.docker.com', 'dockerhub_credentials')
	}

	stage('Deploy')
	{
		//
		sh "docker-compose down"
		sh "docker-compose up -d"
	}

}