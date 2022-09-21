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
# clean up
k delete -f controllers/nginx-deployment.yaml
```

## deployment wordpress

```zsh
k apply -k application/wordpress
# clean up
k delete -k application/wordpress
```

## service

```zsh
k apply -f controllers/nginx-service.yaml
# clean up
k delete -f controllers/nginx-service.yaml
```

## check

```zsh
# デプロイメント一覧確認
k get deployments
# サービス一覧確認
k get services
# ポッド一覧確認
k get pods
# まとめて確認
k get all
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
http://localhost:8001/api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy/#!/login 
# crean up
k -n kubernetes-dashboard delete serviceaccount admin-user
k -n kubernetes-dashboard delete clusterrolebinding admin-user
k delete -f monitoring/crerate-service-account.yaml
k delete -f monitoring/dashboard.yaml
```