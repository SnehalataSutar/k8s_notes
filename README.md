## What is Kubernetes?

Kubernetes (also called K8s) is an open-source platform that helps you automates the deployment, scaling, and management of containerized applications. In simple words, if you're running a lot of apps using containers (like with Docker), Kubernetes helps you organize and control them efficiently just like a traffic controller for your apps.

## K8s architecture 
![Screenshot (130)](https://github.com/user-attachments/assets/cba5f159-346e-4364-8459-2a4945b85e28)
### 1. Control Plane 🧠
This is the brain of your cluster, responsible for managing the overall state and scheduling:

#### API Server
The central access point. Every interaction with Kubernetes—whether from kubectl, a UI, or internal components—goes through the API server. It validates and processes configuration, then stores it in etcd.
#### Scheduler
Create pods at particular time.
#### Controller Manager
Manages actual state and desired state: i.e. Ensure the cluster matches the desired configuration.
#### etcd
A distributed key-value pair that stores all cluster data: resource definitions, current state, secrets, config maps, and more.

### 2. Worker Nodes 🛠️
These nodes run your containerized applications. Each has:
#### Kubelet
Kubelet monitor pods. It checks pod is available or not, if not available it will create pod. 
#### Container Runtime (e.g., Docker, containerd)
Responsible for pulling container images and running container processes.
Creates conteainers in pods.
Decoupled container - More than 1 container.
#### Kube-proxy
Manages internal communication between services and pods (handles forwarding and load-balancing traffic).

## K8s Objects - 

### 1. Pod

A Pod is the smallest unit you can deploy in Kubernetes. It wraps one or more containers that need to run together, sharing the same network and storage. Containers inside a Pod can easily communicate and work as a single unit.

### 2. Node 

A Node is a machine (physical or virtual) in a Kubernetes cluster that runs your applications. Each Node contains the tools needed to run Pods, including the container runtime (like Docker), the Kubelet (agent), and the Kube proxy (networking).

### 3. Cluster

A Kubernetes cluster is a group of computers (called nodes) that work together to run your containerized applications. These nodes can be real machines or virtual ones.

#### There are two types of nodes in a Kubernetes cluster:

#### Master node (Control Plane):
Think of it as the brain of the cluster.
It makes decisions, like where to run applications, handles scheduling, and keeps track of everything.

#### Worker nodes: 
These are the machines that actually run your apps inside containers.
Each worker node has a Kubelet (agent), a container runtime (like Docker or containerd), and tools for networking and monitoring.

### 4. Deployment

A Deployment is a Kubernetes object used to manage a set of Pods running your containerized applications. It provides declarative updates, meaning you tell Kubernetes what you want, and it figures out how to get there.

### 5. ReplicaSet 

A ReplicaSet ensures that the right number of identical Pods are running.

### 6. Service

A Service in Kubernetes is a way to connect applications running inside your cluster. It gives your Pods a stable way to communicate, even if the Pods themselves keep changing.

### 7. Ingress 

Ingress is a way to manage external access to your services in a Kubernetes cluster. It provides HTTP and HTTPS routing to your services, acting as a reverse proxy.

### 8. ConfigMap 

A ConfigMap stores configuration settings separately from the application, so changes can be made without modifying the actual code.

Imagine you have an application that needs some settings, like a database password or an API key. Instead of hardcoding these settings into your app, you store them in a ConfigMap. Your application can then read these settings from the ConfigMap at runtime, which makes it easy to update the settings without changing the app code.

### 9. Secret 

A Secret is a way to store sensitive information (like passwords, API keys, or tokens) securely in a Kubernetes cluster.

### 10. Persistent Volume (PV) 

A Persistent Volume (PV) in Kubernetes is a piece of storage in the cluster that you can use to store data — and it doesn’t get deleted when a Pod is removed or restarted.

### 11. Namespace 

A Namespace is like a separate environment within your Kubernetes cluster. It helps you organize and isolate your resources like Pods, Services, and Deployments.

### 12. Kubelet 

A Kubelet runs on each Worker Node and ensures Pods are running as expected.

### 13. Kube-proxy 

Kube-proxy manages networking inside the cluster, ensuring different Pods can communicate.

