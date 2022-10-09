# environment

```zsh
% kubectl version --client --short
Flag --short has been deprecated, and will be removed in the future. The --short output will become the default.
Client Version: v1.25.2
Kustomize Version: v4.5.7

% helm version --short                          
v3.10.0+gce66412
```

# set hosts
```bash
% cat /etc/hosts
127.0.0.1       gitlab.example.com
127.0.0.1       registry.example.com
127.0.0.1       minio.example.com
```

# deploy using helm

```zsh
helm repo add gitlab https://charts.gitlab.io/
helm repo update
helm upgrade \
  --install gitlab gitlab/gitlab \
  --values gitlab.yaml \
  --timeout 600s
```

# Access

http://gitlab.example.com:32080/

```
kubectl get secret gitlab-gitlab-initial-root-password -ojsonpath='{.data.password}' | base64 --decode ; echo
```

# cleanup

```zsh
helm uninstall gitlab
```