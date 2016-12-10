# Devops lab 2.3 Docker Registry

Working with a Docker registry.

### Step 1

Go to Open the Cloud Platform Console at https://console.cloud.google.com. Go to Compute Engine and VM Instances. Start the VM if it isn’t running and connect using SSH.

### Step 2

Run a Docker registry from an official Registry image

Pull a recent version of the Centos Linux container
* docker pull registry:2

Run the registry in a new Docker container. Expose port 5000
* docker run -d -p 5000:5000 --restart=always --name registry registry:2

### Step 3

Pull another image and store it in the local Registry

Pull a new image from Docker hub
* docker pull ubuntu

Tag the image for the local registry
* docker tag ubuntu localhost:5000/ubuntu

Push the image to the local Registry
* docker push localhost:5000/ubuntu

Remove the image from the local cache
* docker rmi ubuntu

Confirm it has been removed
* docker images

### Step 4

Pull the image from the local registry
* docker pull localhost:5000/ubuntu

Confirm it is in the local cache
* docker images

Run the new image
* docker run --rm -ti localhost:5000/ubuntu /bin/bash

Exit the container
* exit

### Step 5

Clean up artifacts from the lab
* docker rm -f $(docker ps -aq)
* docker rmi $(docker images -q)

Exit the SSH session and stop the VM.

