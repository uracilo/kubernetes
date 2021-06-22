# kubernetes

#Init command
```bash
kubeadm init --apiserver-advertise-address $(hostname -i) --pod-network-cidr 10.5.0.0/16
kubectl apply -f https://raw.githubusercontent.com/cloudnativelabs/kube-router/master/daemonset/kubeadm-kuberouter.yaml
```


# Get general info

```bash
kubectl cluster-info
kubectl get nodes
kubectl get pods
kubectl get deployments
kubectl get services
```

#Mount a service
```bash
kubectl create deployment nginx --image=nginx
kubectl get svc
kubectl expose deployment nginx --type=NodePort --port=80
kubectl get deployments
curl ip:port
```
