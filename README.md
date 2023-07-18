
## Yolo Kubernetes Orchestration
### Description
This project utilizes Kubernetes (K8) to orchestrate the YOLO app on a cluster and expose it for access. YOLO is an application that consists of a client-side and backend component, and this project ensures seamless deployment and management of the app using Kubernetes.

### Setup Instructions
To get started with the YOLO Kubernetes Orchestration, follow the steps below:
1. Ensure that you have `minikube` and `kubectl` aare installed on your local machine. Theser allows you to run Kubernetes clusters locally for testing and development purposes.
2. Clone this repository to your local machine using `git clone <repository-url>`.
3. Start Minikube on your machine. You can use the following command to start Minikube:
```
minikube start
```
4. Navigate to the client and backend directories in the cloned repository.
5. In each directory (client, backend and database), create the necessary Kubernetes manifests:
    - Deployment: Define the desired state and number of replicas for the client, backend and mongo components.
    - Service: Expose the client, backend and mongo components as Kubernetes services.
    - Secrets: Configure any environment-specific secrets or configuration required by the application as defined in the resctive directories secret files.
    - PVC (PersistentVolumeClaim): If applicable, set up persistent storage for the backend component.
    
    You can create the YAML files for these Kubernetes objects based on the requirements of your YOLO app.
6. Apply the Kubernetes manifests using the `kubectl apply` command. For example for the mongo database:
```
kubectl apply -f database/mongo-pv.yaml
kubectl apply -f database/mongo-pvc.yaml
kubectl apply -f database/mongo-secrets.yaml
kubectl apply -f database/deployment.yaml
kubectl apply -f database/mongo-service.yaml
```
7. Access the YOLO app by visiting the link shared on the deployment tab in your Kubernetes UI. Alternatively, you can retrieve the external IP of the client service using the following command:
```
kubectl get services
```

### Technology Used
The YOLO Kubernetes Orchestration project is mainly built using YAML which is commonly used for writing Kubernetes manifests to define the desired state of Kubernetes objects like Deployments, Services, and PersistentVolumeClaims.
