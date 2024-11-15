# A simple Techdome stack application 

### Create a network for the docker containers

`docker network create demo`

### Build the client 

```sh
cd Techdome-frontend
docker build -t Techdome-frontend .
```

### Run the client

`docker run --name=frontend --network=demo -d -p 3000:3000 Techdome-frontend`

### Verify the client is running

Open your browser and type `http://localhost:3000`

### Run the mongodb container

`docker run --network=demo --name mongodb -d -p 27017:27017 -v ~/opt/data:/data/db mongodb:latest`

### Build the server

```sh
cd Techdome-backend
docker build -t Techdome-backend .
```

### Run the server

`docker run --name=backend --network=demo -d -p 5000:5000 Techdome-backend`

## Using Docker Compose

`docker compose up -d`

######################################################################

## Deploy the application using minikube 

## Prerequisites
Ensure you have the following installed:

- Minikube
- Kubectl
- Docker
  
## Step-by-Step Guide
- Start Minikube
```
minikube start
```

## Enable Minikube Docker Environment (optional but helps build images directly in Minikube)
`
eval $(minikube docker-env)
`

## Build Docker Images for frontend and backend services. Navigate to the appropriate directories and build the Docker images.
```
# Build the frontend image
cd Techdome-frontend
docker build -t techdome-frontend:latest .

# Build the backend image
cd ../Techdome-backend
docker build -t techdome-backend:latest .
```

## Deploy to Kubernetes Apply the configurations to the Minikube cluster.
`
kubectl apply -f mongo-deployment.yaml
kubectl apply -f backend-deployment.yaml
kubectl apply -f frontend-deployment.yaml
`

## Check the Status Verify that all pods and services are running.
`
kubectl get pods
kubectl get services
`

## Access the Application

- Use Minikube to find the NodePort for the frontend service:
`
minikube service frontend-service
`
- This command will open the frontend in your default web browser.
