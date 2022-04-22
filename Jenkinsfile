pipeline {
     agent any
     stages {
        stage("Deploy") {
            steps {
                 sh 'sudo cp -r ./* /home/ec2-user/jenkins-react-app-1/'
            }
        }
    }
}
