	ReplicaSet or ReplicaController are kubernetes controller that used to automate scale down or up pods deployment.


**ReplicaSet** is supported in **apps/v1**.  
**ReplicationController** is supported in **v1**.


use below command to get more details about replicaset

```cmd
kubectl explain replicaset 
```



to get replicaset in current namespace:

```cmd
kubectl get replicaset
```


to get replica set details, event logs
```cmd
kubectl describe replicaset [REPLICASET_NAME]
```

to run replica set file from kubernetes client

```cmd
kubectl Create -f [REPLICASET_file]
OR
kubectl apply -f [REPLICASET_file]
```

to reflect files updates to cluster
```cmd
kubectl replace -f [REPLICASET_file]
OR
kubectl apply -f [REPLICASET_file]
```


to edit replica set file from kubernetes client

```cmd
kubectl edit replicaset [REPLICASET_NAME]
```

to scale replica set file from kubernetes client

```cmd
kubectl scale replicaset [REPLICASET_NAME] --replicas=[NEW_REPLICA_NUMBER]
```

to delete replica 

```cmd
kubectl delete replicaset [REPLICASET_NAME]
```


note that you can do **rs** instead of **Replicaset** in commands

Replicaset yaml contain of

* apiVersion: **apps/v1** or **v1**
* Kind: **apps/v1 => Replicaset** or **v1 => ReplicationController**
* metadata: of replicaset like the name of replicaset
* spec: have three sections
	* replicas: how many pods should be deployed ?
	* selector: make sure all pods with same labels in selector equals number of replicas above
	* Template: pod file description

as Example:

```yaml
apiVersion: apps/v1
kind: ReplicaSet
metadata:
  name: replicaset-1
spec:
  replicas: 2
  selector:
    matchLabels:
      tier: frontend
  template:
    metadata:
      lables:
      tier: frontend
    specs:
      containers:
      - name:nginx
      - image: nginx

```
