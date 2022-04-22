pipeline {
     agent any
     stages {
        stage("Deploy") {
            steps {
                 sh 'sudo cp -r /var/lib/jenkins/workspace/jenkinsreactapp/* /home/ec2-user/jenkins-react-app-1/'
            }
        }
    }
}
