pipeline{
    agent any
    stages{
        stage("checkout the code from GitHub Repository"){
            steps{
             git branch: 'main', url: 'https://github.com/UshaPriyanka15/Final-Project.git'
            }
        }
        stage('Build Docker Image') {
          steps{
            script{
              //Build the Docker Image
              sh 'docker build -t my-nginx-app .'
            }
          }
        }
        stage('Run Container') {
          steps{
            script{
             //Stop and remove existing container if it exists
             sh 'docker rm -f my-nginx-container || true'

            //Run the new container
            sh 'docker run -d -p 80:80 --name my-nginx-container my-nginx-app'
            }
          }
        }
        stage('Verify'){
         steps{
          //Simple verification that container is running
          sh 'docker ps | grep my-nginx-container'
         }
        }
}
}
