# SRE/DEVOPS INTERVIEW PREPARATION GUIDE

For last minute preparation/revision for devops/sre interview

### Coding Round:

-   Problem solving
-   Data Structures (List/Array, Dictionary/Hashtables, Set, Tuples, Graph, Tree)
-   OOP
    -   **Abstraction**: Hiding of internal complex details and exposing only necessary information to the user
    -   **Encapsulation**: Wrapping data & code in a single unit, or object, in order to regulate access to the data in a controlled manner.
    -   **Inheritance**: When a child class extends a base/parent class, it inherits the methods & variables of the parent class
    -   **Polymorphism**: When multiple child class extends from a single parent class and have their own implementation of certain methods provided by the base class.
    -   **Composition**: Strong relationship between objects, where the composed object is dependant on the object that is contained within it. E.g Car ---> Engine
    -   **Aggregation**: Weak relationship between objects, when an object refers to another object but can exists independently. E.g Department ---> Employees
    -   **Overloading** **vs Overriding**:
        -   Overloading: Two functions with same name but different number of parameters or type of parameters.
        -   Overriding: Redefinition of a function of a base class function in it's derived class with the same signature.

### DevOps:

-   **Linux Fundamentals**:
    -   **Process vs Thread**: 
        -   Process is a program that is executing. It has a state (running, stopped, terminated) and a process id associated with it.
        -   Thread is a separate flow of execution within a process. Threads help to execute tasks in parallel and improve efficiency.
    -   **systemctl**: command to manage, monitor services on linux
    -   **Journalctl**: command to view logs of running services
    -   **Systemd**: system and service manager for Linux operating systems. Startup, tracking, monitoring/logging of services
-   **Docker**
    -   **Architecture**
        -   Client-server
        -   Docker client talks to Docker daemon. Docker daemon does the building, running and distributing of docker containers
      -   **Docker Image Layers:** Images are built up on layers stacked on each other. Every instruction (FROM, RUN, COPY, ADD) in the Dockerfile creates a layer.
      -   **Docker Multistage:** Use multiple FROM instruction in Dockerfile, and only include the necessary files in the Final Image.
-   **Docker vs Virtual Machine**
    -   **Docker**:
        -   Installed on OS
        -   Shared Kernel
        -   Lighter
        -   Less Isolation
    -   **VM**:
        -   Have it's own OS
        -   Higher Disk Space
        -   Complete Isolation
        -   Can have different OS
-   **Monitoring**
    -   **SLI (Indicator)**
        -   quantitative measure of some aspect of the level of service provided. Common SLIs :
          -   request latency - how long it takes to return a response to a request
          -   error rate - failed request over all requests received
          -   throughput - typically measured in requests per second
          -   availability - proportion of successful requests
    -   **SLO (Objectives)**
        -   target value or range of values for an SLI
    -   **Prometheus**
    -   **Grafana**
-   **AWS**
    -   **LB**
        -   **ALB**:
            -   Used when requirement is advance routing features and support HTTP/HTTPS Traffic
            -   Layer 7 load balancer (Application Layer)
        -   **NLB**:
            -   Used when requirement is high performance, low latency & static IP addresses.
            -   When millions of request are coming per seconds and reliability matters
            -   Layer 4 load balancer (Network Layer)
    -   **Autoscaling group**:
        -   Automatic scaling based on changes in the system or in demand
        -   Health checks: Replace any instance that fails health checks. HA
        -   Protect certain instances from scaling in or out.
    -   **EKS vs ECS**: (Container Orchestration Services)
        -   **EKS**:
            -   Managed Kubernetes
            -   Master node is managed by aws while worker nodes are EC2 instances
            -   Supports multiple container formats
            -   Provides more flexibility and customisation
        -   **ECS**
            -   Managed Docker Service
            -   Containers may run on ec2 or fargate
            -   Specifically for docker
            -   Less customisation options
-   **Terraform**
-   **Ansible**
-   **Helm**

### Kubernetes

-   **Master Node Components:**
    -   **Kubernetes API Server:** The central control point for the Kubernetes cluster, which exposes the Kubernetes API that can be used to manage the cluster.
    -   **etcd:** A distributed key-value store that stores the cluster state, configuration data, and metadata for all Kubernetes objects. (In-memory store)
    -   **Kubernetes Controller Manager:** A component that manages and controls various controllers that are responsible for maintaining the desired state of the cluster.
    -   **Kubernetes Scheduler:** A component that schedules pods to run on nodes based on resource requirements, availability, and other factors.
-   **Worker Node Components:**
    -   **Kubelet:** An agent that runs on each node and is responsible for managing and maintaining the state of pods running on the node.
    -   **Kubernetes Proxy:** A component that runs on each node and is responsible for load balancing network traffic to and from the pods running on the node.
    -   **Container Runtime:** A software component responsible for running containers, such as Docker, containerd, or CRI-O.
-   **Pod:** The smallest deployable unit in Kubernetes, representing a single instance of a container. Pods can contain one or more containers that share the same network namespace and can communicate with each other using localhost.
-   **Deployment:** A higher-level resource that manages the creation, scaling, and update of multiple replicas of a pod. Deployments provide declarative updates to pods and ensure that the desired number of replicas are running at all times.
-   **Service:** An abstract way to expose a set of pods as a network service. Services enable pods to communicate with each other across different nodes and provide load balancing for incoming traffic. Types of load balancer: ClusterIP, NodePort, and LoadBalancer.
-   **ConfigMap:** A way to store configuration data in key-value pairs that can be consumed by a pod or container. ConfigMaps provide a way to decouple configuration data from the application code.
-   **Secret:** Similar to ConfigMaps, but used to store sensitive data such as passwords, keys, and certificates. Secrets are encrypted at rest and can be mounted as files or environment variables in a pod.
-   **StatefulSet:** A resource used to manage stateful applications that require stable network identities and persistent storage. StatefulSets ensure that pods are created in a specific order and have unique hostnames that can be used for stable network identities.
-   **DaemonSet:** A resource used to manage a set of pods that run on every node in a cluster. DaemonSets are typically used for system-level tasks such as log collection or monitoring.
-   **Job:** A resource used to manage batch jobs or one-time tasks. Jobs ensure that a specific number of pods are created to complete a task and can be configured to automatically restart if a pod fails.
-   **CronJob:** A resource used to manage scheduled tasks that run at specific intervals. CronJobs are similar to Jobs, but can be scheduled to run at specific times or intervals using a cron-like syntax.
-   **Namespace:** A way to create virtual clusters within a physical Kubernetes cluster. Namespaces provide a way to partition resources and enable multiple teams or applications to share a cluster without interfering with each other.
-   **Role:** A resource used to define a set of permissions that can be granted to a user or group of users for specific resources within a namespace. Roles are used to control access to resources within a single namespace.
-   **ClusterRole:** Similar to a Role, but applies to the entire cluster instead of a single namespace. ClusterRoles are used to control access to resources across multiple namespaces.
-   **PersistentVolume:** A resource used to represent a piece of external storage that can be used by a pod. PersistentVolumes can be statically provisioned by an administrator, or dynamically provisioned by a storage class.
-   **PersistentVolumeClaim:** A resource used by a pod to request access to a PersistentVolume. PersistentVolumeClaims specify the storage requirements and access mode needed by the pod, and are used by Kubernetes to find a matching PersistentVolume.
-   **Service Discovery in K8s:**
    -   **Service:** Use Kubernetes Service resource for discovering a service. If there's a service name, web-app, in the namespace, default, the the pods exposed by the service can be accessed using the dns `web-app.default` by other resources.
    -   **Environment Vars:** Each service is assigned an environment variable that contains the IP address and port number of the service. Other services can use this environment variable to connect to the service.
-   **HA for K8s Cluster:**
    -   Have multiple master nodes
    -   Master nodes store the state of the cluster in the etcd store and communicate & coordinate with each other accordingly
    -   Recommended to have odd number of master nodes for the following reasons:
        -   To ensure proper quorum, where in a cluster of n nodes, quorum is ceil(n/2 + 1). For e.g n=5, quorum=3.
        -   Reduces split-brain scenarios, where the nodes are not able to reach a decision with regards to who would be the leader
