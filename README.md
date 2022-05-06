## k8s

Kubernetes tips and tricks

### .bashrc

```
# Kubernetes (completion needs Bash 5.1)
source <(kubectl completion bash)
alias k='kubectl'
complete -F __start_kubectl k
source <(k3d completion bash)
source <(helm completion bash)
```

### k3d

```
k3d cluster create --config k3d-one.yaml
export KUBECONFIG=$(k3d kubeconfig merge one)

helm repo add nginx-stable https://helm.nginx.com/stable
helm repo update

helm upgrade --install ingress-nginx ingress-nginx \
  --repo https://kubernetes.github.io/ingress-nginx \
  --namespace ingress-nginx --create-namespace
```
