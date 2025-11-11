
Подключаем репозиторий с чартами
```
helm repo add bitnami https://charts.bitnami.com/bitnami
```
Устанавливаем MySQL чарт из bitnami
```
helm install mysql bitnami/mysql -f mysql-values.yaml
```
Деплоим секреты и приложение
```
kubectl apply -f db-secret.yaml
kubectl apply -f db-configmap.yaml
kubectl apply -f java-app.yaml
kubectl apply -f phpmyadmin.yaml
```
Ставим Ingress
1) Через Minikube
```
minikube addons enable ingress
```
2) Через Helm Chart

```
helm repo add ingress-nginx https://kubernetes.github.io/ingress-nginx
helm repo update
helm install ingress-nginx ingress-nginx/ingress-nginx
```

Применяем Ingress файл

```
kubectl apply -f ingress-rule.yaml
```
Если поменять etc/hosts
```
127.0.0.1   my-java-app.com
```
то можно будет зайти на сайт, а если сделать порт форвардинг, то можно достучаться до phpmyadmin

```
kubectl port-forward svc/phpmyadmin-service 8081:8081
```
