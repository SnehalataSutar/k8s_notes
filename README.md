## What is Kubernetes?

Kubernetes (also called K8s) is an open-source platform that helps you automates the deployment, scaling, and management of containerized applications. In simple words, if you're running a lot of apps using containers (like with Docker), Kubernetes helps you organize and control them efficiently just like a traffic controller for your apps.

### Why kubernates is used:
When you run applications in containers (like Docker), managing them manually can be complex. Kubernetes makes it easier by:

Automatically managing container lifecycles
Scaling applications up or down based on demand
Load balancing traffic between multiple containers
Rolling updates without downtime

### Cluster
A Kubernetes cluster is a group of machines (nodes) that work together to run and manage containerized applications efficiently. It consists of a Control Plane (Master Node) and multiple Worker Nodes that execute the applications.

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
stores key-value type data
Every change in the cluster is recorded in etcd.

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

### ➕ How it all works together
You issue a command via kubectl or UI → it goes to the API Server.

The API Server writes the desired state (e.g., “2 replicas of nginx”) to etcd.

Scheduler assigns Pods to nodes based on resource availability.

Kubelet on the chosen node sees the pending Pod and instructs the container runtime to start it.

Kube-proxy enables network communication so Pods and services can talk to each other.

Controller manager continuously monitors the current state—if a Pod dies, it detects the discrepancy and creates a replacement, ensuring desired uptime.


## K8s Objects - 

### 1. Pod

A Pod is the smallest unit you can deploy in Kubernetes. It wraps one or more containers that need to run together, sharing the same network and storage. Containers inside a Pod can easily communicate and work as a single unit.

A Node is a machine (physical or virtual) in a Kubernetes cluster that runs your applications. Each Node contains the tools needed to run Pods, including the container runtime (like Docker), the Kubelet (agent), and the Kube proxy (networking).

### 2. Service

A Service in Kubernetes is a way to connect applications running inside your cluster. It gives your Pods a stable way to communicate, even if the Pods themselves keep changing.

Types -
1) Cluster IP - Internal communication (pod-to-pod, container-to-container)
2) Node Port - Expose pod on NodeIP
3) Load balancer

### 3. Namespace 

To segregate K8s objects for better identification

### 4. Replica Controller

Controls replicas of pod. It supports equality based selector.

### 5. ReplicaSet 

A ReplicaSet ensures that the right number of identical Pods are running.
Supports mutiple lables.


### 6. Deployment

Controls replicas of pod. It supports equality based selector. It auto updates pods. 

Implements deployment strategies.

1. Rolling Update (Default Kubernetes Deployment Strategy): 
Gradually replaces old pods with new ones, minimizing downtime.
New pods are added while old pods are removed, ensuring a smooth transition.
Kubernetes handles the scaling and termination automatically.

eg.  - If you have 10 pods & set maxsurge to 2 & maxunavailable to 1 k8s will create 2 new pods, terminate 1 old pod & so on.

3. Recreate: 
Terminates all existing pods before deploying the new version.
Simple to implement but can cause downtime.
Suitable for development or when downtime is acceptable.

4. Blue/Green Deployment: 
Maintains two identical environments (blue and green) with different versions.
The new version (e.g., green) is deployed and tested in isolation.
Traffic is switched from the old version (blue) to the new version (green) after successful testing.
Provides a quick rollback option by switching traffic back to the old version if needed.

5. Canary Deployment: 
Gradually shifts traffic to the new version by exposing it to a small subset of users (the "canary").
Monitors the canary's performance and behavior.
If issues arise, the rollout can be stopped or rolled back.
If successful, the new version is gradually rolled out to more users.


### 7. Daemonset 

It will create pod for each node.

### 8. Statefulset

Controls replicas of stateful pods.

### 9. Secret 

A Secret is a way to store sensitive information (like passwords, API keys, or tokens) securely in a Kubernetes cluster.

To encrypt the password - echo -m password | base64

### 10. ConfigMap 

To store variables/environment

A ConfigMap stores configuration settings separately from the application, so changes can be made without modifying the actual code.

Imagine you have an application that needs some settings, like a database password or an API key. Instead of hardcoding these settings into your app, you store them in a ConfigMap. 
Your application can then read these settings from the ConfigMap at runtime, which makes it easy to update the settings without changing the app code.

### 11. Ingress 

For routing (Path based. Source based).

Used to control internal traffic.

### 12. Persistent Volume (PV) 

A Persistent Volume (PV) in Kubernetes is a piece of storage in the cluster that you can use to store data — and it doesn’t get deleted when a Pod is removed or restarted.

