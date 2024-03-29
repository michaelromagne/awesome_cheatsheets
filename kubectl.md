# Kubectl Cheat Sheet

<p align="center">
  <img src="/img/kubectl2.png" width=300 />
</p>

By working with [Okteto](https://github.com/okteto/okteto) then running jobs on Kubernetes clusters, I started to use kubectl. I learned a few useful commands using [RehanSaeed cheatsheet](https://github.com/RehanSaeed/Kubernetes-Cheat-Sheet) and I am centralizing the most common commands here.

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

- Describe a pod (get info from orchestrator, works if pod is evicted)
```
kubectl describe pods <POD_ID>
```

- Get all pods running on gpu nodes
```
kubectl get pods --all-namespaces -o wide |grep delta-sandbox-prod-worker-gpu|grep -v kube-system|grep -v gpu-operator|grep -v prometheus|grep -v cattle|grep Running
```

- Get a shell running inside a pod
```
kubectl exec -it <pod_name> -n <namespace> -- /bin/bash
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

## GPU monitoring

Find the node my container is running on with kubectl get pods then find the exporter that is on the identified node with:
```
kubectl get pods -n gpu-operator -l app=nvidia-dcgm-exporter -o wide
```

## Get memory and cpu used by pod

```
kubectl top pod data-snapshotter-vmpv6-x97jh -n fern --containers
```
And filter accordingly in our gpu monitoring dashboard in the instance filter


