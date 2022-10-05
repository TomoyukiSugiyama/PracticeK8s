# environment

```zsh
% kubectl version --client
% kubectl version --client --short
Flag --short has been deprecated, and will be removed in the future. The --short output will become the default.
Client Version: v1.25.2
Kustomize Version: v4.5.7

% helm version --short                          
v3.10.0+gce66412
```

# deploy using helm

```zsh
helm repo add gitlab https://charts.gitlab.io/
helm repo update
helm upgrade -f gitlab.yaml \
  --install gitlab gitlab/gitlab \
  --timeout 600s
```