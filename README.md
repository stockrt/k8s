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
k3d cluster create one -s 3 -p "8080:80@loadbalancer" -p "8443:443@loadbalancer" --k3s-arg "--no-deploy=traefik@"
#k3d cluster create --config k3d-one.yaml

export KUBECONFIG=$(k3d kubeconfig merge one)

helm upgrade --install ingress-nginx ingress-nginx \
  --repo https://kubernetes.github.io/ingress-nginx \
  --namespace ingress-nginx --create-namespace
```

### nginx-hello app

```
k create namespace nginx-hello-namespace

k apply -f nginx-hello.yaml

echo "127.0.0.1 example.com.br" | sudo tee -a /etc/hosts

open http://example.com.br
```
