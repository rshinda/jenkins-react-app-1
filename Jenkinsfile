pipeline {
     agent any
     stages {
        stage("Build") {
            steps {
                sh "sudo npm install"
                sh "sudo npm run build"
            }
        }
        stage("Deploy") {
            steps {
                 sh 'sudo cp ./src/App.js /home/ec2-user/jenkins-react-app-1/src/App.js'
            }
        }
    }
}
