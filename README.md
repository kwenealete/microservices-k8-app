
This guide provides a step by step instructions for deploying a microservice aplication using a helm chart to  Linode Kubernetes cluster (LKE)

## What is a Microservice?

A microservice is an independently deployable service that performs a specific business function. Unlike monolithic applications, microservices are loosely coupled, allowing for greater flexibility, scalability, and maintainability. They communicate with each other via APIs and can be deployed, scaled, and updated independently.

## Prerequisites

### Before you begin, ensure you have the following installed and configured:
1. Helm – The Kubernetes package manager.
2. kubectl – The Kubernetes command-line tool.
3. Linode Kubernetes Engine (LKE) Cluster – A running cluster with at least one node.
4. Helm Chart – A pre-configured Helm chart for your application.

## step 1

Set up a cluster on the Linode cloud manager with step-by-step guide through the following link : 
https://techdocs.akamai.com/cloud-computing/docs/create-a-cluster

## step 2: Step 2: Connect to Your Linode Kubernetes Cluster

- Download the cluster’s kubeconfig

- Set the KUBECONFIG environment variable:

1: ***chmod 400*** for permission
2: ***'export KUBECONFIG=$(pwd)/kubeconfig.yaml'***

- Verify that you can connect to your cluster:

        ***kubectl get nodes***

If your nodes appear, you have successfully connected.

### step 3: Create helm charts and configure 

- creating helm chart: 'helm create "chart-name"'
- Delete every file inside the template folder and reconfigure it with values and specifications according to your conatiner images/services.
- running shell files: from the project folder run ***./'file-name'***
- install hemlfile: ***brew install helmfile***
- list files in hemlfile: ***hemlfile list***
- run and deploy services to cluster: ***helmfile sync***
- delete files from cluster: ***helmfile destroy***
