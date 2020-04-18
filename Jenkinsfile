pipeline {
     agent any
     stages {
        stage("Checkout") {
            steps {
                git url: 'https://github.com/oshanfernando/jenkins-react-app.git'
            }
        }
        stage("Build") {
            steps {
                sh "sudo npm install"
                sh "sudo npm run build"
            }
        }
        stage("Deploy") {
            steps {
                 echo ${WORKSPACE}
                sh "sudo cp -r ${WORKSPACE}/build/ /var/www/jenkins-react-app/"
            }
        }
    }
}