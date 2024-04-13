[![CircleCI](https://dl.circleci.com/status-badge/img/circleci/BdViYxh9N1av995kReBUH5/EvVhU6g2JWcL3G1D372BD9/tree/master.svg?style=svg)](https://dl.circleci.com/status-badge/redirect/circleci/BdViYxh9N1av995kReBUH5/EvVhU6g2JWcL3G1D372BD9/tree/master)

### Project Summary

This project demonstrates how to operationalize a Machine Learning Microservice API. 

The`sklearn` model that has been trained to predict housing prices in Boston according to several features, such as average rooms in a home and data about highway access, teacher-to-pupil ratios, and so on. Operationalize a Python flask app—in a provided file, `app.py`—that serves out predictions (inference) about housing prices through API calls. 

### Project Steps
* Create a virtualenv with Python 3.7 and activate it.
* Install hadolint and run linting.
* Complete and build DockerFile.
* Deploy Container using Docker.
* Run make predication to test that application runs locally.
* Configured Kubernetes and minicube to create a cluster.
* Deploy the container using Kubernetes and run make predication.
* Deploy working container to Docker repository.
* Run build in CircleCi and demonstrate healty build.

### Setting up our Environment

Create a virtualenv with Python 3.7 and activate it.
python3 -m pip install --user virtualenv
You should have Python 3.7 available in your host. 
Check the Python path using `which python3`
Use a command similar to this one:
python3 -m virtualenv --python=<path-to-Python3.7> .devops
source .devops/bin/activate

* Run `make install` to install the necessary dependencies
Setting up our environment

### Running `app.py`

1. Standalone:  `python app.py`
2. Run in Docker:  `./run_docker.sh`
3. Run in Kubernetes:  `./run_kubernetes.sh`

### Kubernetes Steps

* Setup and Configure Docker locally
* Setup and Configure Kubernetes locally
* Create Flask app in Container
* Run via kubectl

### Commands
1. Clone Repo: `git clone https://github.com/kevmare/Operationalize-a-machine-learning-microservice-API.git`
2. Navigate to directory: `cd DevOps_Microservices/project-ml-microservice-kubernetes`
3. Create a new Virtaul environment: `python3 -m venv ~/.devops` `source ~/.devops/bin/activate`
4. Ensure make is installed: `install make`
5. Install Hadolint:
   ````
       wget -O hadolint https://github.com/hadolint/hadolint/releases/download/v2.7.0/hadolint-Linux-x86_64
       chmod +x hadolint
       sudo mv hadolint /usr/local/bin/
   ````
6. Install kubectl:
   ````
       curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
       chmod +x kubectl
       sudo mv kubectl /usr/local/bin/
   ````
7. Install minikube:
   ````
       curl -Lo minikube https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
       chmod +x minikube
       sudo mv minikube /usr/local/bin/
   ````
8. Run lint: `make lint`
9. Run container: `./run_docker.sh`
10. Make Prediction: `./make_prediction.sh`
11. Upload Docker Image: `./upload_docker.sh`
12. Configure Kubernetes for local: `minikube start`
13. Deploy: `./run_kubernetes.sh`
14. Push to Circleci:
````
       git add .
       git commit -m "New commit"
       git push

````   

### File Contents
````
* /.circlci : YML configuration file for running building pipeline.
* /model_data : Contains model data for making predictions.
* /output_txt_files/Lint Result : Result of lint test.
* /output_txt_files/docker_out.txt : Log output of goodhealth of application interaction.
* /output_txt_files/kubernetes.txt : Log output of make prediction from Kubernetes deployment.
* Dockerfile : Dockerfile for building the image. 
* Makefile : Steps for setup, install and lint tests for environemt.
* app.py : Python flask app that serves out predictions.
* make_prediction.sh : Send a request to the Python flask app to get a prediction.
* requirements.txt : Package dependencies 
* run_docker.sh : File for running docker locally
* run_kubernetes.sh : File to run the app in kubernetes
* upload_docker.sh : File to upload the image to docker
````


