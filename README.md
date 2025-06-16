<b>What is Kubernetes?</b>

Kubernetes (also called K8s) is an open-source platform that helps you automates the deployment, scaling, and management of containerized applications. In simple words, if you're running a lot of apps using containers (like with Docker), Kubernetes helps you organize and control them efficiently just like a traffic controller for your apps.

<b> K8s architecture </b>

<b> K8s Objects - </b>

<b> 1. Pod</b>

A Pod is the smallest unit you can deploy in Kubernetes. It wraps one or more containers that need to run together, sharing the same network and storage. Containers inside a Pod can easily communicate and work as a single unit.

<b> 2. Node </b>

A Node is a machine (physical or virtual) in a Kubernetes cluster that runs your applications. Each Node contains the tools needed to run Pods, including the container runtime (like Docker), the Kubelet (agent), and the Kube proxy (networking).

<b> 3. Cluster</b>

A Kubernetes cluster is a group of computers (called nodes) that work together to run your containerized applications. These nodes can be real machines or virtual ones.

<b>There are two types of nodes in a Kubernetes cluster:</b>

<b> Master node (Control Plane):</b>
Think of it as the brain of the cluster.
It makes decisions, like where to run applications, handles scheduling, and keeps track of everything.

<b>Worker nodes: </b>
These are the machines that actually run your apps inside containers.
Each worker node has a Kubelet (agent), a container runtime (like Docker or containerd), and tools for networking and monitoring.

<b> 4. Deployment</b>

A Deployment is a Kubernetes object used to manage a set of Pods running your containerized applications. It provides declarative updates, meaning you tell Kubernetes what you want, and it figures out how to get there.

<b> 5. ReplicaSet </b>

A ReplicaSet ensures that the right number of identical Pods are running.

<b> 6. Service </b>

A Service in Kubernetes is a way to connect applications running inside your cluster. It gives your Pods a stable way to communicate, even if the Pods themselves keep changing.

<b> 7. Ingress </b>

Ingress is a way to manage external access to your services in a Kubernetes cluster. It provides HTTP and HTTPS routing to your services, acting as a reverse proxy.

<b> 8. ConfigMap </b>

A ConfigMap stores configuration settings separately from the application, so changes can be made without modifying the actual code.

Imagine you have an application that needs some settings, like a database password or an API key. Instead of hardcoding these settings into your app, you store them in a ConfigMap. Your application can then read these settings from the ConfigMap at runtime, which makes it easy to update the settings without changing the app code.

<b> 9. Secret </b>

A Secret is a way to store sensitive information (like passwords, API keys, or tokens) securely in a Kubernetes cluster.

<b> 10. Persistent Volume (PV) </b>

A Persistent Volume (PV) in Kubernetes is a piece of storage in the cluster that you can use to store data — and it doesn’t get deleted when a Pod is removed or restarted.

<b> 11. Namespace </b>

A Namespace is like a separate environment within your Kubernetes cluster. It helps you organize and isolate your resources like Pods, Services, and Deployments.

<b> 12. Kubelet </b>

A Kubelet runs on each Worker Node and ensures Pods are running as expected.

<b> 13. Kube-proxy </b>

Kube-proxy manages networking inside the cluster, ensuring different Pods can communicate.

