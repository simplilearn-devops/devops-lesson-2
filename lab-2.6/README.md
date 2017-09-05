# Exercise 7.4 Docker Compose

Use Docker Compose to manage a container.

### Step 1

Start and connect to your Google Compute Engine virtual machine.

Download the docker-compose executable.  
`cd`  
`mkdir bin`  
`curl -L "https://github.com/docker/compose/releases/download/1.9.0/docker-compose-$(uname -s)-$(uname -m)" -o bin/docker-compose`  
`chmod +x bin/docker-compose`  

### Step 2

Change to the exoercise directory.  
`cd`
`cd devops-lesson-7/lab-7.4`  

Look at the Dockerfile.  
`cat Dockerfile`  

Build the Docker image.  
`docker build -t centos-sshd .`  

### Step 3

Run the image.  
`docker run -d --name sshd -p 2222:22 centos-sshd`  
`docker ps`  

Connect to the ssh server.  
`ssh -p 2222 student@localhost`  
Answer `yes` to accept the RSA key.  
Give the password `student`.  
Verify that you are logged into the server.  
Log out with control-D.  

Stop the server.  
`docker rm -f sshd`  

### Step 4

Look at the Docker Compose YAML file.  
`cat docker-compose.yml`  

The directory `sshd` is a build directory containin g a copy of the Deckerfile.  
Start the server.  
`~/bin/docker-compose up -d`  
`~/bin/docker-compose ps`

Connect to the ssh server.  
`ssh -p 2222 student@localhost`  
Give the password `student`.  
Verify that you are logged into the server.  
Log out with control-D.  

Stop the server.  
`~/bin/docker-compose down`  
`~/bin/docker-compose ps`  

### Step 5

Disconnect from the virtual machine.  
Stop the virtual machine.  

