# jenkins-docker
Docker image for jenkins with docker support    
##Note-  Chnage the line `docker-ce=17.12.1~ce` depending on ther version of docker client you need to use.

Step-1: Build the docker image.
This Dockerfile will use a Jenkins container as a base image and then install the docker client , So that it can communicate with the docker daemon.

Build the image with below command

$ docker image build -t jenkins-docker .

Note: Change the version of docker inside the Dockerfile based on your own requirements.

Step-2: Start the container with mounted docker daemon
After successfully building the container in step 1 we need to run the container with mounted docker daemon

$ docker container run -d -p 8080:8080 -v /var/run/docker.sock:/var/run/docker.sock jenkins-docker

Note: The docker daemon running on host machine must be compatible with docker client running in Jenkins container. check the version of the host with docker --version and install the appropriate version of docker client inside the Jenkins container.

Conclusion:
Your Jenkins container now should have a functional docker installation. verify it by running

docker container ls

From inside the Jenkins container. The output should have same as running docker container ls from the docker host.
