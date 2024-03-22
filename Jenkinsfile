node {
    def app
    stage('Clone repository') {
        checkout scm
    }
    stage('Build image') {
       app = docker.build("dejans12/devops")
    }
    stage('Push image') {   
               // signal the orchestrator that there is a new version
        
    }
}