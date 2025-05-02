- A DaemonSet in Kubernetes is a way to ensure that a specific pod runs on every node in your cluster . This is useful for tasks that need to be performed on each node, like logging or monitoring agents(prometheus,Nodeexporter). When you create a DaemonSet, Kubernetes automatically schedules the pod to run on any new nodes added to the cluster. If a node is removed, the pod on that node is also removed.
  
- Daemonset vs Deployment
1. DaemonSet:
Runs a pod on every node (or selected nodes).
Good for things like logging or monitoring.
You don’t scale it; it just runs on each node.
------------
3. Deployment:
Manages a group of identical pods.
Used for applications that can scale up or down.
You can adjust how many pods are running as needed.
- eg : kubectl create deployment metrics --image nginx --replica 3
above example creates 3 pods but nt all nodes are used

- But demonset make sure run one pod one node eg: collecting metrics from each node

- mounting these two volumes /proc and /sys  are two virtual file systems in Linux that allow users and programs to interact with the kernel and access various system information in a convenient way .
-
- both these virtual file systems are read only and the information they provide is generated dynamically by the kernel when accessed, because we need system level metrics we need to mount these two folders to our container as these folders are present in every node we are giving this as host path

