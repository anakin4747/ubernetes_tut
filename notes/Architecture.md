# K8s Architecture

# Worker Machine in K8s Cluster

Each worker node has multiple application pods on it.

Each worker node must have 3 processes installed.

    - Container runtime (ie Docker)
    - Kubelet - interfaces with node and container runtime
    - Kube proxy - for inter node communication/synchronization

# Master Processes

Master nodes oversee worker nodes ensuring their functionality.

Each master node must have 4 processes installed.

    - API server - what we interact with to control the cluster
                 - authentication
    - Scheduler - processes applications and schedules them to worker nodes
                - only decides which node should the pod run on it doesn't actually start it,
                  the kubelet process on the worker node starts the pod
    - Controller manager - monitors for dead nodes
                         - if it finds dead pods it sends a request to the scheduler to restart pods
    - etcd - key value store
           - cluster brain
           - cluster changes get stored in the key value store
           - application data is not stored in etcd

In practice its common to have multiple master nodes

The API server is load balanced across the master nodes.

The etcd is distributed storage across all master nodes.