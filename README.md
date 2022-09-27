# PracticeK8s

## .zshrc

```zsh
source <(kubectl completion zsh)
alias k=kubectl
compdef __start_kubectl k
```

## deploy nginx

```zsh
k apply -k controllers
# clean up
k delete -k controllers
```

## deploy wordpress

```zsh
k apply -k application/wordpress
# clean up
k delete -k application/wordpress
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
# シークレット確認
k get secrets
# PersistentVolume 確認
k get pvc
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

## debug

```zsh
# debugging pods
k describe pods
# debugging services
k get endpoints
# create a shell
k exec -it nginx-deployment-XXXXXXXXXXXX -- sh
```

## fields
* apiVersion ・・・ 利用する KubernetesAPI のバージョン
* kind ・・・ オブジェクトの種類
* metadata ・・・ オブジェクトを一意に識別するための情報、文字列の name 、 UID 、または任意の namespace 
* spec ・・・ オブジェクトの望ましい状態

サンプル
```yaml
apiVersion: v1
kind: Service
metadata:
  name: nginx-service
spec:
  type: LoadBalancer
  ports:
    - protocol: TCP
      port: 8080
      targetPort: 80
  selector:
    app: nginx
```