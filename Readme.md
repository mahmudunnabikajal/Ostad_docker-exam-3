#### You are part of a DevOps team responsible for deploying a new microservices-based application on a Kubernetes cluster. The application has multiple services, each running in its own container. It needs persistent storage for uploaded files and must be highly available and scalable.

---

**Question 1:** Describe how you would set up the Kubernetes cluster to meet these requirements. Discuss the roles of nodes (both Master and Worker), and explain how Kubernetes will manage the containers to ensure high availability and scalability.

**Ans:** For highly available and scalable microservices-based application, I will setup a single master node(Control Panel Node) with multiple worker nodes to maintain high availability. Because the master node is responsible for distributing the network requests to the worker's node, so if one worker node fails other worker nodes will handle those requests and the master node will always distribute the network request because if the master node fails due to high network requests then other worker nodes will fail. Will use "Kubernetes Deployment" to manage the Pod replica set, and state of services. This Deployment service will monitor the service state and if one replica set fails then it will automatically create a new one to fulfill the requirements.


---
**Question 2:** The application’s uploaded files requires persistent storage. How would you utilize Persistent Volume Claims (PVCs) to provide this? Explain how Kubernetes handles the lifecycle of these volumes and ensures that the data remains consistent and available, even if a container or node fails.

**Ans:** For handling persistent storage to uploaded files will use PersistentVolumeClaim to bind Persistent Volumes. This PVC will make sure to be available across pod restarts or node failures. Kubernetes will manage the lifecycle of the PVCs to ensure high-availability storage even if nodes/pods fail.


---
**Question 3:** The team decides to use a specific container runtime for this deployment. What considerations would you take into account when choosing a container runtime? How does Kubernetes interact with the runtime to manage the lifecycle of your containers?

**Ans:** For container runtime, we have to check the compatibility with Kubernetes. Most common is Containerd for its simplicity. Other runtimes like Docker Engine. Kubernetes interacts with the runtime through the kubelet, which uses CRI to manage container lifecycles, such as starting and stopping containers, monitoring their health, and pulling container images, etc.
