pipeline{
agent any
stages{
	stage('Initialize'){
        def dockerHome = tool 'myDocker'
        env.PATH = "${dockerHome}/bin:${env.PATH}"
    }
	stage('Build')
	{
		steps
		{
		sh'''
		docker version
		docker info
		docker compose version
		'''
		}
	}
}
}