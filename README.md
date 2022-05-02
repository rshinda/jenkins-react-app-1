
# Create a jenkins pipeline to deploy change

Upload you code to git  
Use jenkins to do new deployment on ec2 instance.  
Configure git webhooks  to Trigger you jenkins jobs  
So whenever new code will upload on git, jenkins deployment should happen on Ec2 server to push new code.

1) First create instance type and selcect instance type t3.medium
Update the available packages and their version 
```
sudo yum update -y
```
2) Install Node.js on Amazon linux
```
sudo yum install -y gcc-c++ make

curl -sL https://rpm.nodesource.com/setup_14.x | sudo -E bash - 

sudo yum install -y nodejs 
```
Check Version of node Also, check the version of npm.
```
node -v  
npm  -v
```
3) Now let’s install Nginx webserver
```
 sudo amazon-linux-extras list | grep nginx
 
 sudo yum -y install nginx
 
 sudo systemctl start nginx

 sudo systemctl status nginx
```
 4) Create the react project. (create-react-app)
```
npx create-react-app
```
 clone ur git  
```
git clone https://github.com/sudheergiri/jenkins-react-app-1.git
```
here you can see all files like jenkins file.

Then go inside your directory  #cd jenkins-react-app-1
and run
```  
 npm install
 ```
   it will install node_modules folder

after run
```  
npm run build
```
 it will install build folder  

Run the project
```
npm start
```
After you enter the command, you’ll be able to see the react server running and the relevant ports in the shell.

Now try to access the react app using the public IP for your server. Note: the port should be opened in the security group as below. If the port is not allowed, add an inbound rule to your security group.

Then try to access the react app with the IP address and the port number. http://<IP-address>:3000/. You should see the react app as below.

*After installing Nginx, let’s configure Nginx to serve the react application on port 80.

cd /etc/nginx      
then go inside the conf.d file 

create conf file and place the below config
```
server {                                                                 
listen 80;                                                               
                                                                         
  server_name Your-server-ip;                                             
                                                                         
                                                                         
  access_log /var/log/nginx/reat-tutorial.com.access.log;                
  error_log /var/log/nginx/reat-tutorial.com.error.log;                  
location / {                                                             
    proxy_pass http://<local-ipaddress>:3000;                                 
    proxy_http_version 1.1;                                              
    proxy_set_header Upgrade $http_upgrade;                              
    proxy_set_header Connection 'upgrade';                               
    proxy_set_header Host $host;                                         
    proxy_cache_bypass $http_upgrade;                                    
  }                                                                      
}
```
In order to make sure the configuration syntax is correct. Use the below command,
```
sudo nginx -t 
```
Now you should be able to access the react app using the server IP address (http port). No other ports will be used.

5) pm2 setup

use commands 
```
serve 

serve -s build

pm2 serve build 80 --spa

sudo npm install pm2@latest -g

pm2 start App.js

pm2 status 
```
6) Download and install Jenkins

To download and install Jenkins:

To ensure that your software packages are up to date on your instance, use the following command to perform a quick software update:
```
$ sudo yum update –y
```
Add the Jenkins repo using the following command:
```
$ sudo wget -O /etc/yum.repos.d/jenkins.repo \
    https://pkg.jenkins.io/redhat-stable/jenkins.repo
```
Import a key file from Jenkins-CI to enable installation from the package:
```
$ sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io.key

$ sudo yum upgrade
```
Install Java:
```
$ sudo amazon-linux-extras install java-openjdk11 -y
```
Install Jenkins:
```
$ sudo yum install jenkins -y
```
Enable the Jenkins service to start at boot:
```
$ sudo systemctl enable jenkins
```
Start Jenkins as a service:
```
$ sudo systemctl start jenkins
```
You can check the status of the Jenkins service using the command:
```
$ sudo systemctl status jenkins
```
7) Configure Jenkins
Jenkins is now installed and running on your EC2 instance. To configure Jenkins:

Connect to http://<your_server_public_DNS>:8080 from your favorite browser. You will be able to access Jenkins through its management interface:

8) As prompted, enter the password found in /var/lib/jenkins/secrets/initialAdminPassword.

Use the following command to display this password:
```
$ sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```
Copy the alphanumeric terminal 32-character password and paste into the Administrator Password field, then click Continue. 

And select certain plugins:

once your jenkins is ready  ,,Hit Start using Jenkins button and it will take you to the Jenkins dashboard. 

9) Create New item: Click on the New Item on the left-hand side of the dashboard.

 Fill the project description: 

You can enter the job details as per your need.    

10) Source Code Management: 

Under source code management, enter the repository URL.
You can also use a Local repository. 

11) Branches to build select the master

12) Script Path   selcet jenkins file 

13) Save the project: 

Click Apply and save the project. 

14) Build Source Code and check its status: 

Click on “Build Now” on the left-hand side of the screen to create the source code

15) Console Output: 

Select the build number and click on “Console Output” to check the status of the build run. 

When it shows success, it means that we have successfully run the program from the GitHub Repository. 

congratualation your jenkins pipeline running successfully.
-
