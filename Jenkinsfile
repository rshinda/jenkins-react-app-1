pipeline {
     agent any
     stages {
        stage("Deploy") {
            steps {
                 sh 'sudo scp ./jenkins-react-app-1/* /home/ec2-user/jenkins-react-app-1'
            }
        }
    }
}
