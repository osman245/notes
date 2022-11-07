### Create and Config Pods

### ReplicaControllers(legacy)

- Have a single pod running in a node, if the pod crashes, we lose the containers in the pod.

- ReplicationController controls the amount of pods running at the same time in the node..

- To load balance and scale we use additional nodes as well, expanding our replication controller access..

- replication controller is legacy, we use replica set now...
