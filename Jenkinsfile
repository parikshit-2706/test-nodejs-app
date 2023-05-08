pipeline { 
  
   agent any

   stages {
   
     stage('Install Dependencies') { 
        steps { 
           sh 'npm install' 
        }
     }
     
     stage('Test') { 
        steps { 
           sh 'echo "testing application..."'
        }
      }

         stage("Deploy application") { 
         steps { 
           sh 'echo "deploying application..."'
         }

     }
     
     stage('Build Docker Image') {
        steps {
            script {
                sh 'docker build -t parikshit2097/mynodejsapp-1.0 .'
            }
        }
     }
     
     stage("Push Docker image") {
        steps {
            script {
                withCredentials([string(credentialsId: 'parikshit2097', variable: 'dockerhubpwd')]) {
                    sh "docker login -u parikshit2097 -p ${dockerhubpwd}"
                }
                sh "docker push parikshit2097/mynodejsapp-1.0"
            }
        }
     }
  
   }
}
