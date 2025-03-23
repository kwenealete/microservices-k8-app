
This guide provides a step by step instructions for deploying a microservice aplication using a helm chart to  Linode Kubernetes cluster (LKE)

## What is a Microservice?

A microservice is an independently deployable service that performs a specific business function. Unlike monolithic applications, microservices are loosely coupled, allowing for greater flexibility, scalability, and maintainability. They communicate with each other via APIs and can be deployed, scaled, and updated independently.





1. Introduction

We will deploy a microservice application on a Linode server using Kubernetes, package the application using Helm, and deploy using Helmfile. Helmfile simplifies managing Helm releases, making deployments efficient and repeatable.

By the end, you will have:
✅ A Kubernetes cluster running on a Linode server 
✅ A Helm chart for deploying your microservice
✅ A Helmfile configuration to automate deployments

⸻

2. Prerequisites

Ensure you have:
- A Linode account: A cloud computing provider offering virtual servers.
- Helm: A package manager for Kubernetes that simplifies deployments.
- Helmfile: A tool for managing multiple Helm charts efficiently.
- Docker: A platform to containerize applications for easy deployment.
- Git: Version control system used for managing project repositories.

On your local machine, you need:
- kubectl The command-line tool to interact with Kubernetes clusters.

### Install kubectl
macOS:

Install via Homebrew:
``` bash
brew install kubernetes-cli
```
Linux:

Download the latest kubectl release:

``` bash
curl -LO https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl
```

Make the downloaded file executable:
``` bash
chmod +x ./kubectl
```

Move the command into your PATH:
``` bash
sudo mv ./kubectl /usr/local/bin/kubectl
```

3. Set Up Linode kubernetes engine (LKE) 

https://techdocs.akamai.com/cloud-computing/docs/getting-started-with-lke-linode-kubernetes-engine


Once your LKE cluster is created :
4. Go to Kubernetes > Your Cluster > Download Kubeconfig and safe the kubeconfig.yaml file on your computer

5. Export the kubeconfig environment variable to use this file and connect to the cluster

``` bash
export KUBECONFIG=~/<config-file-location>/kubeconfig.yaml
```

View your cluster's nodes using kubectl.
``` bash 
kubectl get nodes
```

## Install Helm

https://helm.sh/docs/intro/install/

## Install helmfile
``` bash
brew install helmfile
```

## Deploy the microservice app 

``` bash 
helmfile sync
```

check releases 
``` bash
helmfile list
```
view app on the browser

Go to your Linode account > NodeBalancers and copy the IP Address. Paste it on your browser and view the app.

To destroy the deployment 
``` bash
helmfile destroy

```
