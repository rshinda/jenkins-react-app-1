pipeline {
     agent any
     stages {
        stage("Deploy") {
            steps {
                 sh 'sudo cp ./public/* /home/ec2-user/jenkins-react-app-1/public'
            }
        }
    }
}
