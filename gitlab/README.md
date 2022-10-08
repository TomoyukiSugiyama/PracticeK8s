# environment

```zsh
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
helm upgrade \
  --install gitlab gitlab/gitlab \
  --values gitlab_config.yaml \
  --timeout 600s

helm upgrade --install gitlab gitlab/gitlab \
  --timeout 600s \
  --set global.hosts.domain=example.com \
  --set global.hosts.externalIP=127.0.0.1 \
  --set certmanager-issuer.email=me@example.com
```

# cleanup

```zsh
helm uninstall gitlab
```