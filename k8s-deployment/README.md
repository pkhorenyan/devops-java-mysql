
Подключаем репозиторий с чартами
```
helm repo add bitnami https://charts.bitnami.com/bitnami
```
Устанавливаем MySQL чарт из bitnami
```
helm install my-sql -f mysql-values.yaml
```

Деплоим секреты и приложение
```
kubectl apply -f db-secret.yaml
kubectl apply -f db-config.yaml
kubectl apply -f java-app.yaml
kubectl apply -f phpmyadmin.yaml
```
Ставим Ingress

```
minikube addons enable ingress
```
Устанавливаем Nginx Ingress

```
helm repo add ingress-nginx https://kubernetes.github.io/ingress-nginx
helm repo update
helm install ingress-nginx ingress-nginx/ingress-nginx
```

Применяем Ingress файл

```
kubectl apply -f ingress-rule.yaml
```