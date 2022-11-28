# Monitor & Logging

### Monitoring kubernetes

- we monitor to build analytics upon the data..
- heapster: deprecated
- metrics servers are the way to go (promethus( non in-memory metrics) and etc)

- 1 metric server per kubernetes cluster.
- monitors nodes and pods , aggregrates them and stores metrics in 
in-memory.

- kubelet acts as an agent in each node...
- kubelet has a cAdvisor subcomponent which retrieves and exposes performance metrics through kubeapi to make metrics
possible for the metric server 

- To enable the metrics server do ...

```minikube addons enable metrics-server```

- if you dont have minikube do ...

```git clone https://github.com/kodekloudhub/kubernetes-metrics-server.git```
- then cd into the repository and do kuebctl create -f . , to create all the pods through the pod definition files existing in the directory.



**commands for performance metrics**
- kubectl top node --> get the nodes performance metrics
- kubectl top pod --> get the pods performance metrics


### Managing Logs

- In docker we can stimulate random events  using 
docker run -d kodekloud/event-simulator.

do docker logs -f ecf
- to see the live log trail 

**in kubernetes**
- We can create a pod using the kodekloud/event-simulator image
  

name of file: event-sim.yaml
```
apiversion: v1
kind: Pod
metadata:
  name: event-sim-pod
spec:
  containers:
  - name: event-simulator
    image: kodekloud/event-simulator
  - name: image-processor
  - image: some-image-processor
  ``` 
kubectl create -f event-sim
kubectl logs -f event-sim  ```-f to stream logs live```
kubectl logs -f <pod name> <enter image you want to log in your pod>

- you can either log a pod or a node...