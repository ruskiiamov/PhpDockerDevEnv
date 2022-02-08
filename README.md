Установить 
[Docker](https://docs.docker.com/engine/install/ubuntu/)
и
[Docker-Compose](https://docs.docker.com/compose/install/)

Создать файл .env с помощью .env.example:
- APP_PATH - путь к папке проекта
- DOCUMENT_ROOT - путь к папке с index.php в проекте

Перед первым запуском и после каждого изменения конфигурации нужно пересобрать образ:
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
Вход в командную строку контейнера php:
```
docker-compose exec php bash
```
Сomposer нужно запускать в командной строке контейнера php:
```
docker-compose exec php bash
composer install
...
exit
```

URL: [http://localhost:8080](http://localhost:8080)

Подключение к локальной БД MySQL:
- Для подключения внешнего клиента:
  - Host: localhost
  - Port: 33060
- Для подключения в коде внутри контейнера php:
  - Host: mysql
  - Port: 3306
- User: root
- Password: root

Для подключения к удаленной БД нужно пробросить порт в контейнер php.
Например для подключения к БД с хостом 10.10.80.XX:3306, который доступен для сервера
192.168.0.XX с входом по ssh через порт 22:
```
docker-compose exec php bash
ssh -f -N -L 9999:10.10.80.XX:3306 username@192.168.0.XX -p22
...
exit
```
После этого удаленная БД будет доступна внутри контейнера php на 127.0.0.1 через порт 9999