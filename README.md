# itmo_containers


В docker-compose описаны 3 сервиса 
1) Postgres образ базы данных Postgres с хранением данных в папке ./data/db 
2) init-db инит сервис, запускающий файл initproject.sh, который в свою очередь пытается создать схему в бд, после старты и перехода контейнера postgres в статус healthy
3) card-service, билдищий Dockerfile и присваивающий этому образу имя card-service-container, стартует после успешного старта postgres

Переменные для БД хранятся в файле .env  
Общая netwrok -- product_cars_service_net

# Ответы на вопросы

1) Можно ли ограничивать ресурсы (например, память или CPU) для сервисов в docker-compose.yml? Если нет, то почему, если да, то как?  
    Можно, к описанию сервисов сегментов
```yaml
services:  
    card-service:  
        deploy:  
            resources:  
                limits:  
                    cpus: 0.50  
                    memory: 512M  
            reservations:  
                    cpus: 0.25  
                    memory: 128M  
```

2) Как можно запустить только определенный сервис из docker-compose.yml, не запуская остальные?  
Прописать имя сервиса docker-compose up -d [SERVICE]. В моем примере docker-compose up -d postgres запусит только образ базы данных