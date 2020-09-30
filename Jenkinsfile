pipeline
{
 environment
 {        
    dockerImage = ''
 }
 agent any
 parameters{
 	string(name : 'Image', defaultValue : '', description: 'This is name of Image to be pushed to Docker Registry')
 }
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
        dockerImage = docker.build "${params.Image}"+":$BUILD_NUMBER"
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
        docker.withRegistry('http://172.20.149.107:5000')
        {
          dockerImage.push()
        }
      }
    }
   }
 }

}