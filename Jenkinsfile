node {
   def registryProjet='https://hub.docker.com/limam1984/presentations-jenkins/wartest'
   def IMAGE="${registryProjet}:wartest-version-${env.BUILD_ID}"
    stage('Clone') {
      git 'https://github.com/limammedsaid/war-build-docker.git'
    }
    
    stage('Maven Package') { 
         sh label: '', script: 'mvn package'
    }
    def img = stage ('Build')
       docker.build("$IMAGE", '.')
    
     stage('Push') {
          docker.withRegistry('https://hub.docker.com', 'reg1') {
              img.push 'latest'
              img.push()
          }
    }

}