# Cluster Maintainance


### OS Upgrade

- Whenever a node goes offline, the master node gives
it 5 minutes to determine if its dead.

- If a node goes down.. its pods are not available...

if there's a pod in that down node that is not apart of a replicaset, then that pod is forever gone.


- kubectl drain node-1 (no pods can be scheduled on node1,its pods are moved gracefully to other nodes)
- kubectl cordon node-2(marks a node, unschedulable)
- kubectl uncordon node-1(for pods to be scheduled again on that drained node) 

in the default kubernetes cluster there are two nodes..

**Questions**
- Q4) kubectl drain node01 --ignore-daemonsets
- 