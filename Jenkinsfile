node {
    def app
    stage('Clone repository') {
        checkout scm
    }
    stage('Build image') {
       app = docker.build("dejans12/devops")
    }
    stage('Push image') { 
	if (env.BRANCH_NAME == 'dev') {  
       		docker.withRegistry('https://registry.hub.docker.com', 'dejan-dockerhub') {
           	app.push("${env.BRANCH_NAME}-${env.BUILD_NUMBER}")
            	app.push("${env.BRANCH_NAME}-latest")
            	// signal the orchestrator that there is a new version
           }
	else
	{
		echo "Skipping image push. Changes are not on the 'dev' branch."
	}
    }
}
