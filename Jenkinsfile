pipeline {
     agent any
     stages {
        stage("Build") {
            steps {
                sh "sudo npm install"
                sh "sudo npm run build"
                sh "npm start"
            }
        }
        stage("Deploy") {
            steps {
                 sh 'sudo cp /var/lib/jenkins/workspace/jenkinsreactapp/src/App.js /home/ec2-user/jenkins-react-app-1/src/App.js'
            }
        }
    }
}
