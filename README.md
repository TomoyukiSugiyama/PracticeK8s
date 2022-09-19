# PracticeK8s

## .zshrc

```zsh
source <(kubectl completion zsh)
alias k=kubectl
compdef __start_kubectl k
```

## deployment

```zsh
k apply -f controllers/nginx-deployment.yaml
```
## service

```
k apply -f controllers/nginx-service.yaml
```

## check

```zsh
# デプロイメント一覧確認
k get deployments
# サービス一覧確認
k get services
# ポッド一覧確認
k get pods
```

## monitoring

```zsh
# deploy dashboard
k apply -f monitoring/dashboard.yaml
# create service account
k apply -f monitoring/crerate-service-account.yaml
# getting token
k -n kubernetes-dashboard create token admin-user
# proxy
k proxy
# access
http://localhost:8001/api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy/ 
```