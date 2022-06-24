node {
   def registryProjet='registry.gitlab.com/xavki/presentations-jenkins/wartest'
   def IMAGE="${registryProjet}:wartest-version-${env.BUILD_ID}"
    stage('Clone') {
      git 'https://github.com/limammedsaid/AWS_Job_Maven_Docker.git'
    }
    stage('Maven Package') { 
       sh label: '', script: 'mvn package'
    }
    
    
    def img = stage ('Build') {
       agent {
         docker { image '$IMAGE' }
        }
    }
     stage('Push') {
          docker.withRegistry('https://hub.docker.com', 'reg1') {
              img.push 'latest'
              img.push()
          }
    }

}