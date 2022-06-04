pipeline {
     agent any
     stages {
          stage("Build") {
               steps {
                    sh "sudo npm install"
                    sh "sudo npm run build"
               }
          }
      }   
     stages {
        stage("Deploy") {
            steps {
                 sh 'sudo cp -r ./* /home/ec2-user/jenkins-react-app-1/'
            }
        }
    }
}
