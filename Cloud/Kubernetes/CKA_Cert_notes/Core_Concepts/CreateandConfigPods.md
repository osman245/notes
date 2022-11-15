### Create and Config Pods

### ReplicaControllers(legacy)

- Have a single pod running in a node, if the pod crashes, we lose the containers in the pod.

- ReplicationController controls the amount of pods running at the same time in the node..

- To load balance and scale we use additional nodes as well, expanding our replication controller access..
  ![LoadBalancing_Scaling.jpg](LoadBalancing_Scaling.jpg)

![img.png](replicacontroller1.png)

- Replication controller is legacy, we use replica set now...
- Now we use replicaSet

![replicaset.png](replicaset.png)

- In replica sets we require selectors.
- Selectors use labels so we know namespace to replicate the pods..
- To scale for more replicas of a pod we can update the yaml file
- Labels are properties that we can attach to each item for example for their type, kind, and so on. Selectors help us in finding these items. You can think of a selector as a filter. We could label pods based on some attributes i.e. app name, front-end, back-end.(copied)
  **Ways to Scale..**
- kubectl edit to edit the existing running replicaset.
- kubectl replace -f <enter yaml file>
- kubectl scale --replicas=6 -f replicaset-definition.yml // can do it from the command line, if replicaset hasnt been created yyet.
- kubectl scale --replicas=6 replicaset myapp-replicaset
  **Other commands in kubectl**
- kubectl get replicaset-- get all ReplicaSets in the default namespace.
- kubectl explain replicaset | grep VERSION ===> gives you the version of replicaset
- kubectl create -f <yaml file> to create any kubernetes resource...
- kubectl delete <resource> <resource name>
- kubectl edit replicaset <replicaset> then do ...

- Replicaset makess sure that theres always the specified num of pods are running, that were identified in the yaml file.

### Deployment
