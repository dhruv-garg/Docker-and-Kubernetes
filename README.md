<h1>Introdution to Microservices, Docker and Kubernetes</h1>

<h3>Getting Started</h3>

**Definitions:**

Microservice: A microservice is a software developemtn technique that structures an application as a collection of loosely coupled services.

Docker: Docker is an open platform for developers and sysadmins to build, ship, and run distributed applications, whether on laptop, data center VM's or the cloud.

Kubernetes: Kuberenets is an open source system for automating deployment, scaling and management of containerized applications.

For more detail refer: https://kubernetes.io/docs/concepts/overview/what-is-kubernetes/

Let's start with docker:

**Commands:**

-> docker

Make sure you have docker installed, if not follow up with this link:

https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-16-04

-> sudo docker ps

Gives info about containers running on docker

If we wish to see working of docker, we could run a sample container

**Command:** sudo docker run -d -p 3000:80 tutum/hello-world

This maps port 3000 on our machine to port 80 on this container

Now if we do docker ps again, this container will be found running

Now after this is done, let's deploy containers on Kubernetes.

**Prerequisites:**

1) Minikube: Minikube is a tool that makes it easy to run Kubernetes locally.

2) Kubectl: Kubectl is a command line interface for running commands against Kubernetes cluster.

3) Virtual Machine: Minikube uses a VM layer on Linux, it does so to provide a well known and tested environment for Kubernetes to run in.

Install these 3 things to continue.

**Great!** It's time to boot up the minikube

-> minikube start

Proceed further with creating a deployment file (yml or json) format.

-> sudo kubectl get pods

To check if there are any existing pods running

->sudo kubectl get deployments

To check if there any deployments already

-> minikube dashboard

Opens up a GUI application to interact with cluster

Now cd to the directory where deployment.yml file has been created.

But before creating deployement, we need to create the image of application which our deployemtn.yml file will fetch from docker hub. In this case, checkout line 35 which states the name, that is the name of the image we need to create.

**Creating image:**

Follow up with steps metioned:

Create a directory by mkdir where all files are to be kept.

cd into the drectory

-> npm init

Press enter several times

Then,

-> npm i express --save

Edit package.json file.

-> touch index.js

*For creating image can also refer to this **link***: https://nodejs.org/en/docs/guides/nodejs-docker-webapp/

Now we need to containerise this, so we need a Docker File

-> touch Dockerfile

Create the Dockerfile

-> touch .dockerignore

Here we mention the modules or file to be ignored when copying.

Now to build this,

-> sudo docker build -t dhruvgarg/exampleapp:v1.0.0 .

Here dhruvgarg is my username of dockerhub account, you can use yours

Now to check if its running,

-> sudo docker run -p 8080:8080 dhruvgarg/eampleapp:v1.0.0

Push file to dockerhub

-> sudo docker psuh dhruvgarg/exampleapp:v1.0.0

Create deployement using kubectl

-> sudo kubectl create -f deployment.yml

Check if the deployment if running successfully or not

-> minikube dashboard

**Source** - *Youtube James Quigley*:
**https://www.youtube.com/watch?v=1xo-0gCVhTU&t=1015s&list=LLjdqfK_xlZcRbrythgwYdTA&index=6**
