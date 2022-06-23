node {
    stage('Clone') {
      git 'https://github.com/limammedsaid/AWS_Job_Maven_Docker.git'
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