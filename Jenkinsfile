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
                 sh ' cp ./src/App.js /home/ubuntu/jenkins-react-app-1/src '
            }
        }
    }
}
