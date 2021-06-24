# Kubernetes

## Installing kubernetes dependencies

### Windows

`$ > choco install minikube`
`$ > choco install kubernetes-cli`

## Running locally

### Starting minikube

`$ > minikube start`

### Using a local docker image

`$ > minikube docker-env | Invoke-Expression`
`$ > docker build -t {image_name} .`

> Set the image name in the yaml file to use it, and set `image-pull-policy` as Never.

## Annotations

### What is minikube?

> minikube is local Kubernetes, focusing on making it easy to learn and develop for Kubernetes.

### Kubernetes cli

#### CRUD commands

`$ > kubectl create deployment [name]`
`$ > kubectl edit deployment [name]`
`$ > kubectl delete deployment [name]`

#### List components

`$ > kubctl get [nodes | pod | services | deployment]`

#### Debugging pods

`$ > kubectl logs [name]`
`$ > kubectl exec -it [name] -- bin/bash`
`$ > kubectl describe pod [name]`

#### Using configuration file for CRUD

`$ > kubectl apply -f [filanme]`
`$ > kubectl delete -f [filanme]`

### Namespaces

`$ > kubectl create namespace [name]`
`$ > kubectl get namespace`

## Ingress

### What is Ingress?

> It is a service that will provide routing rules to manage external users' access to the services in a Kubernetes cluster, typically via HTTPS/HTTP.

### Windows

> In Windows, we need to open a tunnel with minikube to be able to access what we defined in Ingress configurations. First, we need to apply the following Ingress configuration to let us able to open the tunnel.

`$ > kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v0.47.0/deploy/static/provider/cloud/deploy.yaml`
`$ > minikube tunnel`

### Host registering

> After the deployment of an ingress component, you will need to update the file `C:\Windows\System32\drivers\etc\hosts` to map the IP from ingress with the defined host.
> You should add the bottom of the file something like this:
> `127.0.0.1 {host}`

### Getting docker image from private registry

`$ > kubectl create secret docker-registry <name> --docker-server=DOCKER_REGISTRY_SERVER --docker-username=DOCKER_USER --docker-password=DOCKER_PASSWORD --docker-email=DOCKER_EMAIL`
