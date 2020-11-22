# k3s-test
k3s
```
curl -sfL https://get.k3s.io | INSTALL_K3S_VERSION=v1.19.3+k3s2 INSTALL_K3S_EXEC='--flannel-backend=none --no-flannel' sh -
```

Install helm 

```
curl https://raw.githubusercontent.com/helm/helm/master/scripts/get-helm-3 | bash
```

Setup Helm repository

```
helm repo add cilium https://helm.cilium.io/
```

Install cilium with the portmap plugin enabled
```
KUBECONFIG=/etc/rancher/k3s/k3s.yaml helm install cilium cilium/cilium --version 1.9.0 --namespace=kube-system --set cni.chainingMode=portmap
```

```
kubectl get pods --all-namespaces -o custom-columns=NAMESPACE:.metadata.namespace,NAME:.metadata.name,HOSTNETWORK:.spec.hostNetwork --no-headers=true | grep '<none>' | awk '{print "-n "$1" "$2}' | xargs -L 1 -r kubectl delete pod
```


### kubectl

```
kubectl -n kube-system get pods -l k8s-app=cilium
```

```
kubectl apply -f apps/nginx.yaml
```

```
kubectl get pods -l app=nginx
```

```
kubectl create -f cilium_policies/deny.yaml
```

```
kubectl exec -it -n kube-system cilium-cxpxm -- cilium status
```

### cilium commands

```
kubectl exec -n kube-system  cilium-cxpxm -- cilium policy get
```



