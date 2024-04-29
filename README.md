
# Kubernetes Project

This repository contains Kubernetes manifests for deploying a MongoDB database and a Mongo Express web interface for managing the database.

## Prerequisites

- Kubernetes cluster
- `kubectl` CLI installed and configured to use the cluster
- Basic knowledge of Kubernetes resources

## Usage

### 1. Create MongoDB Deployment

Apply the MongoDB deployment manifest:

```bash
kubectl apply -f mongo.yaml


2. Create Secrets for MongoDB
Create a secrets file mongo-secret.yaml with encoded username and password:

echo -n 'username' | base64
echo -n 'password' | base64

  
Apply the secret:
kubectl apply -f mongo-secret.yaml

3. Create MongoDB Internal Service
This service allows other pods to communicate with the MongoDB deployment.

Apply the service manifest:
kubectl apply -f mongo-internal-service.yaml


4. Create Mongo Express Deployment, External Service, and ConfigMap
Create a ConfigMap for the MongoDB URL and apply it:
kubectl apply -f mongo-express-configmap.yaml

Create the Mongo Express deployment:
kubectl apply -f mongo-express.yaml


5. Access Mongo Express
To access Mongo Express from a browser, create an external service with a load balancer:

kubectl apply -f mongo-express-external-service.yaml


Configuration
Before applying the manifests, make sure to update the following:

MongoDB Username and Password: Update mongo-secret.yaml with your MongoDB username and password.
Mongo Express Database Connection: Update mongo-express.yaml with the correct database address, username, and password.
Mongo Express ConfigMap: Update mongo-express-configmap.yaml with the correct MongoDB URL.

Author
Danyal Khanzada

License
This project is licensed under the MIT License.

This README provides a comprehensive guide for setting up MongoDB and Mongo Express on Kubernetes. You may need to adjust it according to your specific configuration.





    Commands:
    1. Kubectl apply -f [File name]
    2. To see if the service is attached to correct pod
     - Kubectl describe service [filename]
    3. kubectl get pod -o wide
    