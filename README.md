## k3d Multi-Node Cluster Setup
Welcome to the k3d multi-node cluster setup guide! This repository provides a comprehensive guide on how to create and manage a multi-node Kubernetes cluster using k3d.
> k3d is a lightweight wrapper to run k3s (Rancher's minimal Kubernetes distribution) in Docker. It is designed to be simple, efficient, and easy to use, making it a great tool for local development and CI/CD pipelines.
## Why k3d?
**k3d makes it easy to create and manage lightweight Kubernetes clusters. Here are a few reasons why you might want to use k3d** :
  - **Lightweight and Fast** : k3d runs k3s in Docker, which is much lighter than a full-fledged Kubernetes setup.
  - **Simple Setup** : With just a few commands, you can have a fully functional Kubernetes cluster up and running.
  - **Local Development** : Perfect for developing and testing Kubernetes applications locally.
  - **CI/CD Integration** : Easily integrate k3d into your CI/CD pipelines to test your Kubernetes manifests and configurations.
## Features
  - **Multi-Node Clusters** : Set up multi-node clusters to simulate real-world Kubernetes environments.
  - **Custom Configurations** : Customize your cluster with different node configurations and network settings.
  - **Port Forwarding** : Easily forward ports from your host machine to your cluster nodes.
  - **Volume Mounting** : Mount local directories into your cluster nodes for persistent storage.
  - **Cluster Management** : Simple commands to start, stop, delete, and list clusters.
## Prerequisites
Before you begin, make sure you have the following installed:
  - Docker
  - k3d (v5.0.0 or later)
## Create a Multi-Node Cluster
* To create a multi-node cluster, you can use the `k3d cluster create mycluster --servers 3 --agents 3` command. This creates a cluster with 3 server (control plane) node and 4 agent (worker) nodes.
## Advanced Configuration
 * For more advanced configurations, such as specifying details for k3d cluster creation,load balancer, control plane nodes, worker nodes, and essential Kubernetes components. Here's a sample k3d cluster configuration YAML file :
```
apiVersion: k3d.io/v1alpha2
kind: Simple
name: mycluster
servers: 3
agents: 4
ports:
  - port: 80:80
  - port: 443:443
    nodeFilters:
    - loadbalancer

```
**Then create the cluster using the configuration file:**
```
k3d cluster create --config k3d-config.yaml
```
## Verify the Cluster
**Once the cluster is created, you can verify it using the following commands** :
1. List the clusters: 
```
k3d cluster list
```

2. Get the cluster status:
```
kubectl get nodes
```
You should see your server and agent nodes listed and ready.
> [!NOTE]
> Replace **'mycluster'** with the name of your cluster if you used a different name.

*Now, you can use `kubectl` commands to interact with your k3d cluster just like any other Kubernetes cluster.*


