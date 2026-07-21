Kubernetes Basics

This section explains the main Kubernetes components and their basic purpose.

Main Tools

Kubernetes

Kubernetes is a platform used to automate the deployment, management, and scaling of containerized applications.

kubectl

"kubectl" is the Kubernetes command-line tool. It is used to communicate with and manage a Kubernetes cluster.

kubectl get pods
kubectl get services
kubectl get deployments

Minikube

Minikube creates a local Kubernetes cluster. It is useful for learning and testing Kubernetes on your computer.

minikube start
minikube status
minikube stop

Main Kubernetes Components

1. Pod

A Pod is the smallest visible unit in Kubernetes.

It contains one or more containers that run together. Containers inside the same Pod share the same network and IP address.

A Pod's IP address is temporary. When the Pod is recreated, its IP address can change. For this reason, applications normally communicate through a Service.

kubectl get pods
kubectl describe pod <pod-name>

2. Service

A Service provides a stable IP address and DNS name for a group of Pods.

The Service sends traffic to the correct Pods even when their IP addresses change.

There are services for internal communication and services that can expose an application outside the cluster.

kubectl get services
kubectl describe service <service-name>

3. Ingress

Ingress manages external HTTP and HTTPS traffic.

It can route requests to different Services using a domain or URL path while keeping the other parts of the cluster private.

Example:

example.com/api → Backend Service
example.com/app → Frontend Service

4. Volumes

Volumes are used to store data outside the container's temporary filesystem.

They help preserve data when a container or Pod is restarted.

Volumes are especially important for databases and applications that need persistent data.

5. Secrets

Secrets store private values, such as:

- Passwords
- API keys
- Database credentials

Secrets use key-value pairs. Their values are normally stored using Base64 encoding.

«Base64 encoding is not encryption. Sensitive values still need to be protected.»

Secrets can be added to containers as environment variables or mounted files.

6. ConfigMap

A ConfigMap stores non-sensitive configuration values using key-value pairs.

Examples:

- Application environment
- API URLs
- Feature flags
- Configuration options

ConfigMaps should not be used for passwords or private information.

7. Deployment

A Deployment is a blueprint that describes how Kubernetes should create and manage Pods.

A Deployment YAML file can include:

- Container image
- Application name
- Environment variables
- Number of replicas
- Ports
- Update strategy

kubectl get deployments
kubectl apply -f deployment.yml
kubectl delete -f deployment.yml

Example structure:

apiVersion: apps/v1
kind: Deployment
metadata:
  name: example-app
spec:
  replicas: 2
  selector:
    matchLabels:
      app: example-app
  template:
    metadata:
      labels:
        app: example-app
    spec:
      containers:
        - name: example-app
          image: example-image:latest

8. StatefulSet

A StatefulSet is similar to a Deployment, but it is designed for stateful applications.

It gives each Pod:

- A stable name
- Stable storage
- A predictable creation order

StatefulSets are commonly used for databases and distributed systems.

Basic Architecture

External User
      |
   Ingress
      |
   Service
      |
 Deployment
      |
     Pods
      |
 Containers

"Kubernetes components" (image.png)

Useful Commands

# View cluster information
kubectl cluster-info

# View all main resources
kubectl get all

# View Pods
kubectl get pods

# View Services
kubectl get services

# View Deployments
kubectl get deployments

# Apply a YAML file
kubectl apply -f file.yml

# View detailed information
kubectl describe pod <pod-name>

# View container logs
kubectl logs <pod-name>

# Delete a resource from a YAML file
kubectl delete -f file.yml