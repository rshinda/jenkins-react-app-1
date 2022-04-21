pipeline {
     agent any
     stages {
        stage("Build") {
            steps {
                sh "sudo npm run build"
            }
        }
        stage("Deploy") {
            steps {
                 sh 'sudo cp ./src/* /home/ec2-user/jenkins-react-app-1/src/'
            }
        }
    }
}
