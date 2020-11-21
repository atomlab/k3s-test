# k3s-test
k3s
```
curl -sfL https://get.k3s.io | INSTALL_K3S_VERSION=v1.19.3+k3s2 INSTALL_K3S_EXEC='--flannel-backend=none --no-flannel' sh -
```
install cilium
```
kubectl create -f https://raw.githubusercontent.com/cilium/cilium/v1.9/install/kubernetes/quick-install.yaml
```

```
kubectl get pods --all-namespaces -o custom-columns=NAMESPACE:.metadata.namespace,NAME:.metadata.name,HOSTNETWORK:.spec.hostNetwork --no-headers=true | grep '<none>' | awk '{print "-n "$1" "$2}' | xargs -L 1 -r kubectl delete pod
```

install helm 

```
curl https://raw.githubusercontent.com/helm/helm/master/scripts/get-helm-3 | bash
```

### kubectl

```
kubectl -n kube-system get pods -l k8s-app=cilium

```

### cilium commands

```
```
```

```
