# Pods
The atomic unit of deployment in Kubernetes.  Pods may consist of 1 or more containers.  

## Definitions
* Scheduling - The assignment of the pod to a node. Even if it fails, this instance of the pod is never moved to other nodes, as is the case with CPU processes, but a new pod instance may be created to replace it.
* 

## Mental Model
Each pod can be thought of as a separate logical computer that contains one application.  The application can consist of a single process running in a container, or a main application process and additional supporting processes, each running in a separate container.

Each pod has its own IP, hostname, processes, network interfaces and other resources. Containers that are part of the same pod think that they’re the only ones running on the computer.

## Namespaces
All of the containers in a pod share network and UTS Linux namespaces.  Certain features are available when specific namesapces are shared:
* Network namespace: both containers use the same network interfaces, share the same IP address and port space
* UTS namespace: both see the same system hostname



