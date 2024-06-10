
# Шаг 1 запускаем миникуб
minikube start --force

![start_minikube.png](screenshots%2Fstart_minikube.png)

# Шаг 2 Собираем кастомный образ card-service из ЛР2
eval $(minikube docker-env)
docker build -t card-service:latest .

# Шаг 3 Добавляем манифесты

kubectl create -f pg_configmap.yml
kubectl create -f pg_secret.yml
kubectl create -f pg_deployment.yml
kubectl create -f pg_service.yml
kubectl create -f card-service.yml

Деплоймент образа postgres и образа card-service с init-контейнеров из ЛР2

![add_manifests.png](screenshots%2Fadd_manifests.png)

# Шаг 4 проверяем логи card-service 
![card-service_logs.png](screenshots%2Fcard-service_logs.png)
Убеждаемся, что приложение на spring стартовало успешно
# Шаг 5 прокидываем порт, для проверки ручек сервиса
kubectl port-forward --address localhost deployment/card-service 8083:8080

![ports.png](screenshots%2Fports.png)

# Шаг 6 дергаем ручку через постман, для проверки сервиса

![postman.png](screenshots%2Fpostman.png)

Создание карточек происходит успешно на порту 8083