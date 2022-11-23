- Kubectl get pods
  to check what pods are in the main cluster

- Kubectl get pods -o wide
  to get additional info on the pods

- Kubectl run nginx - image=nginx
  (to run a pod with a nginx container in kubernetes)

- Kubectl describe pod webapp
  get info on the pod webapp

- kubectl delete pod webapp
  delete pod

- kubectl run redis --image=redis  
  un a pod named redis with the image redis

  **-dry-run=client flag to preview the object that would be sent to your cluster, without really submitting it.**

- kubectl run redis --image=redis123 --dry-run=client -o yaml (put in console) > redis-definition.yaml (now put in file)
  create a manifest yaml file... that runs redis...

- kubectl create -f redis-definition.yaml (now create pod)

