# Kubernetes Cheat Sheet

Recently I began working with [Okteto](https://github.com/okteto/okteto) to spawn VMs in a Kubernetes cluster and train Fraud Detection models with more computing power, in a replicable environment.
It was the occasion for me to start playing with Kubernetes. I learned a few useful commands using [RehanSaeed cheatsheet](https://github.com/RehanSaeed/Kubernetes-Cheat-Sheet).

I'll centralize the few commands I actually use here.

## Cluster info

- Get cluster names
```
kubectl config get-clusters
```

- Get cluster info
```
kubectl cluster-info
```

## Get contexts

- Get list of contexts.
```
kubectl config get-contexts
```

## Get all

- Get all info about things running : pods, services, daemonsets, deployments, replicasets, statefulsets, cronjobs, jobs...
```
kubectl get all (--all-namespaces) (-n namespace)
```

## Services

- Get services running
```
kubectl get services (--all-namespaces) (-n namespace)
```

- Forward ports for a service running in your namespace
```
kubectl port-forward svc/<service_name> <port>
```

## Pods 

- get list of pods running
```
kubectl get pods (--all-namespaces) (-n namespace)
```

- Describe a pod
```
kubectl describe pods <POD_ID>
```

## Logs

- Get logs for a pod or a service
```
kubectl logs <POD_ID>
```

## Delete Command

```
kubectl delete nodes <NODE_ID>
kubectl delete pods <POD_ID>
kubectl delete svc <SVC_ID>
```

If you delete delete a pod without deleting its higher level controller (deployment, replicaset), Kubernetes will respawn it automatically. For instance, with Okteto, deleting a pod will spawn an identical pod if you do not delete the associated deployment.

## Scaling and autoscaling

Some commands exist for scaling or autoscaling, but I have not tried yet. To be tested


