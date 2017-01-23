# Devops Lab 2.1 Docker

These instructions will guide you through the process of using Docker.

## Connect to the virtual machine.

### Step 1 

Open the Cloud Platform Console at https://console.cloud.google.com.

Click on the three horizontal bars at the left most side of the blue bar near the top
of the browser window. _Select Compute Engine_.

Select _VM Instances_. You should see the virtual machine you created earlier.

### Step 2

Click on the checkbox to the left of the VM name and then select _START_. It will take a few moments to start up.

Click on _SSH_ to start a terminal window.

## Working with Docker.

### Step 1

Test that Docker has been installed correctly on your computer

The GCE image you used to create this computer already has Docker installed.
Check to see the version of Docker  
`docker --version`

### Step 2

Pull a pre-built Docker image with a very light weight operating system installed
by pulling the latest version of the Alpine Linux distribution container  
`docker pull alpine`

Notice the size of this image  
`docker images`

Run a container based on this image, Give the container the name "client",
and activate the command shell processor  
`docker run -it --name client alpine /bin/sh`

Explore the Alpine Linux distribution by executing various Linux commands
`date`  
`pwd`  
`whoami`  

Do any additional exploration you may want to do

Change to the root user's directory  
`cd`

Touch a file to create it in the root directory
`touch testfile`

Exit the container  
`exit`

View the running containers (you should see none as you exited the last container)  
`docker ps`

View all containers.  
You will see a non-running but still available container named "client"  
`docker ps -a`

Restart the container  
`docker restart client`

Connect your terminal to the running container  
`docker attach client`

Verify that the file you placed in the root directory is still there  
`cd`
`ls -la`

Exit   
`exit`

Now delete the container  
`docker rm client`

### Step 3

Pull a pre-built Docker image with a heavier weight operating system  
Pull the latest version of the Debian Linux distribution container  
`docker pull debian`

Notice the size fo this image and compare it with Alpine  
`docker images `

Run a container based on this image and activate the command shell processor  
`docker run --rm -ti debian /bin/bash`

Explore the Debian Linux distribution by executing various Linux commands  
`date`  
`time`  
`pwd`  
`whoami`  

Exit the container  
`exit`

### Step 4

Run a container with a program already installed.  
Pull the hello-world image.  
`docker pull hello-world`

Run the hello-world container and program.  
`docker run hello-world`

### Step 5

Clean up after the labi.  
`docker rm -f $(docker ps -aq)`  
`docker rmi $(docker images -q)`  

