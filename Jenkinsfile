pipeline
{
 environment
 {
    image = '172.20.149.107:5000/dockerdemo3'        
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
        dockerImage = docker.build image+ ":$BUILD_NUMBER"
        echo "Say Hello to me"
      }
    }
   }
   stage('Deploy image to Docker Hub')
   {
    steps
    {
      script
      {
        docker.withRegistry( 'http://172.20.149.107:5000')
        {
          dockerImage.push()
        }
      }
    }
   }
 }

}