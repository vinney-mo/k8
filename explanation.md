
## Yolo Kubernetes Orchestration
The application make used two docker images (backend and client) along with MongoDB on Kubernetes. This will creation several Kubernetes resources, including Deployments, Services, PersistentVolume (PV), PersistentVolumeClaim (PVC), and Secrets.

### Choice of Kubernetes Objects for Deployment:

##### Deployments:
These provide a declarative way to define the desired state of the application and handle replica pod management. Using Deployments ensures that the desired number of replicas are running, and Kubernetes takes care of scaling, updating, and rolling back the application when needed. In this scenario we have deployment for `backend`, `client` and the `mongo`

##### Services:
These are essential for exposing the backend and client applications to other components within the Kubernetes cluster. By creating Services, we ensure that the pods can be accessed using a consistent DNS name and IP.

##### StatefulSets: 
For the MongoDB database, we'll use a StatefulSet. StatefulSets are ideal for applications that require stable, persistent storage, like databases. StatefulSets provide unique identities and stable hostnames for each replica pod, which is crucial for databases that need to maintain data integrity during scaling and updates.

#####  Secrets:
Kubernetes Secrets to store sensitive information like database passwords and API keys. In this project we use them to store the mongodb user login credential for the databse in `mongo-secret`, the mongo db url that is used in the backend deployements in the `backend-secret` togthere with the port on which the backend service should run in and `client-secret` to store the backend url used for requests fron the client

### Exposing Pods to Internet Traffic:
Exposing pods to traffic in Kubernetes is done through Kubernetes Services. It provides a stable endpoint (IP address and DNS name) that allows other components within or outside the cluster to access the pods. Tthe project makes used of a `LoadBalancer` type of Services in Kubernetes.

### Use of Persistent Storage:
For the MongoDB database, to ensure persistent storage for data integrity it will use Kubernetes PersistentVolume (PV) and PersistentVolumeClaim (PVC). The PersistentVolume is a cluster-wide resource that represents a physical storage device, while the PersistentVolumeClaim is a request for storage by a pod. The PVC binds to the PV, providing a reliable storage solution for MongoDB data.

### Git Workflow:
The K8 files are version-controlled using Git alongside other project files, and changes are be committed and pushed to a Git repository.
