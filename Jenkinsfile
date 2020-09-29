pipeline
{
 environment
 {
    registry = "172.20.149.107:5000/docker2demo"
    registryCredential = ''
    dockerImage = ''
 }
 agent any
 stages
 {
   stage('Git Step')
   {
    steps
    {
     git 'https://github.com/Shreyash-Talwekar/dockerdemo.git'
    }
   }
   stage('Build Image')
   {
    steps
    {
      script
      {
        dockerImage = docker.build registry+ ":$BUILD_NUMBER"
      }
    }
   }
   stage('Deploy image to Docker Hub')
   {
    steps
    {
      script
      {
        docker.withRegistry( '', registryCredential )
        {
          dockerImage.push()
        }
      }
    }
   }
 }

}