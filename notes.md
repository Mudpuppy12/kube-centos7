# Master node


[kube-apiserver]

kube-apiserver exposes the Kubernetes API; it is the front-end for the Kubernetes control plane. It is designed to scale horizontally (i.e., one scales it by running more of them– Building High-Availability Clusters).

[etcd]
etcd is used as Kubernetes’ backing store. All cluster data is stored here. Proper administration of a Kubernetes cluster includes a backup plan for etcd’s data.

kube-controller-manager
kube-controller-manager is a binary that runs controllers, which are the background threads that handle routine tasks in the cluster. Logically, each controller is a separate process, but to reduce the number of moving pieces in the system, they are all compiled into a single binary and run in a single process.

These controllers include:
       * Node Controller: Responsible for noticing & responding when nodes go down.
       * Replication Controller: Responsible for maintaining the correct number of pods for every replication controller object in the system.
       * Endpoints Controller: Populates the Endpoints object (i.e., join Services & Pods).
       * Service Account & Token Controllers: Create default accounts and API access tokens for new namespaces.
       * ... and others.

[kube-scheduler]
kube-scheduler watches newly created pods that have no node assigned, and selects a node for them to run on.

[cloud-controller-manager (1.6)]
cloud-controller-manager is a binary that runs controllers that interact with the underlying cloud providers. The cloud-controller-manager binary is an alpha feature introduced in Kubernetes release 1.6.

These Controllers include:
	* Node Controller: For checking the cloud provider to determine if a node has been deleted in the cloud after it stops responding
	* Route Controller: For setting up routes in the underlying cloud infrastructure
	* Service Controller: For creating, updating and deleting cloud provider load balancers
	* Volume Controller: For creating, attaching, and mounting volumes, and interacting with the cloud provider to orchestrate volumes

# Node Componets

[kubelet]
kubelet is the primary node agent. 
It Watches for pods that have been assigned to its node (either by apiserver or via local configuration file) and:

* Mounts the pod’s required volumes
* Downloads the pod’s secrets
* Runs the pod’s containers via docker (or, experimentally, rkt).
* Periodically executes any requested container liveness probes.
* Reports the status of the pod back to the rest of the system, by creating a “mirror pod” if necessary.
* Reports the status of the node back to the rest of the system.

[kube-proxy]
kube-proxy enables the Kubernetes service abstraction by maintaining network rules on the host and performing connection forwarding.

[docker]
docker is of course used for actually running containers.
