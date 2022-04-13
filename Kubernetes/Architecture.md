# Architecture

## Cluster
The set of machines that compose the Kubernetes installation

## Node
Also known as worker node, [Nodes](https://kubernetes.io/docs/concepts/architecture/nodes/) host the [[Pods]] that are the components of the application workload. 
## Control Plane
The [control plane](https://kubernetes.io/docs/reference/glossary/?all=true#term-control-plane) manages the worker nodes and the Pods in the cluster.  

## Kubelet
The [kubelet](https://kubernetes.io/docs/reference/command-line-tools-reference/kubelet/) is the primary "node agent" that runs on each node. It can register the node with the apiserver using one of: the hostname; a flag to override the hostname; or specific logic for a cloud provider.

## Container Runtime Interface (CRI)
The [CRI](https://kubernetes.io/docs/concepts/architecture/cri/) is a plugin interface which enables the kubelet to use a wide variety of container runtimes, without having a need to recompile the cluster components.  You need a working [container runtime](https://kubernetes.io/docs/setup/production-environment/container-runtimes) on each Node in your cluster, so that the [kubelet](https://kubernetes.io/docs/reference/generated/kubelet) can launch [[Pods]] and their containers.

The Container Runtime Interface (CRI) is the main protocol for the communication between the kubelet and Container Runtime.