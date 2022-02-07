Установить 
[Docker](https://docs.docker.com/engine/install/ubuntu/)
и
[Docker-Compose](https://docs.docker.com/compose/install/)

Создать файл .env с помощью .env.example:
- APP_PATH - путь к папке проекта
- DOCUMENT_ROOT - путь к папке с index.php в проекте

Перед первым запуском и после каждого изменения конфигурации:
```
docker-compose build
```
Запуск контейнеров:
```
docker-compose up -d
```
Остановка контейнеров:
```
docker-compose down
```
Использование composer:
```
docker-compose exec php bash
composer install
...
exit
```

URL: [http://localhost:8080](http://localhost:8080)

Подключение к MySQL:
- Host: localhost
- Port: 33060
- User: root
- Password: root

Для использования своего проекта нужно заменить значения переменных APP_PATH 
и DOCUMENT_ROOT в файле .env
