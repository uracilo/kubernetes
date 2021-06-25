# kubernetes

## Init command
```bash
kubeadm init --apiserver-advertise-address $(hostname -i) --pod-network-cidr 10.5.0.0/16
kubectl apply -f https://raw.githubusercontent.com/cloudnativelabs/kube-router/master/daemonset/kubeadm-kuberouter.yaml
```


## Get general info

```bash
kubectl cluster-info
kubectl get nodes
kubectl get pods
kubectl get deployments
kubectl get services
```
## service yaml

```yaml
## Mount a service
apiVersion: apps/v1
kind: Deployment
metadata:
  labels:
    app.kubernetes.io/name: load-balancer-example
  name: hello-world
spec:
  replicas: 5
  selector:
    matchLabels:
      app.kubernetes.io/name: load-balancer-example
  template:
    metadata:
      labels:
        app.kubernetes.io/name: load-balancer-example
    spec:
      containers:
      - image: gcr.io/google-samples/node-hello:1.0
        name: hello-world
        ports:
        - containerPort: 8080
```

```
kubectl apply -f load-balancer-example.yaml

kubectl apply -f https://k8s.io/examples/service/load-balancer-example.yaml

```

```
kubectl get deployments hello-world
kubectl describe deployments hello-world
```


```
kubectl get replicasets
kubectl describe replicasets
```

```
kubectl expose deployment hello-world --type=LoadBalancer --name=my-service
```

```
kubectl get services my-service
```

```
kubectl describe services my-service
```


```
kubectl get pods --output=wide
```
## Consulta

```
curl http://<external-ip>:<port>
```

## Limpieza

```
kubectl delete services my-service
kubectl delete deployment hello-world
```





