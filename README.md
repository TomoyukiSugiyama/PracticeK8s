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

## check

```zsh
# デプロイメント一覧確認
k get deployments
# サービス一覧確認
k get services
# ポッド一覧確認
k get pods
```