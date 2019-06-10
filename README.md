### Начало работы
- Склонируйте репозиторий 
```
sudo git clone name repository
```
- Переименуйте папку в домен сайта 
```
sudo mv docker-symfony site_domain
```
- Выполните настройку окружения

Перейдите в папку проекта

- Создай проект
```
composer create-project symfony/skeleton app
```

Откройте файл `.env` . Задайте домен, проверьте версию PHP,измените пароли на бд(особенно для прод окружения)!
```
cd site_domain
sudo nano .env
```
```
URL=site domain            # Домен сайта (используеться для создания записи на прокси и генерации сертификата)

# MySQL settings           # Доступы к бд 
MYSQL_DATABASE=database name
MYSQL_USER=database user
MYSQL_PASSWORD=database password
MYSQL_ROOT_PASSWORD=database root password

# Site path
SITE_PATH=./app
```
- Разрешите доступ на запись для РНР
```
sudo chmod -R 777 app
```
- Запустите контейнеры
```
docker-compose up -d
```
Чтобы проверить, что все сервисы запустились посмотрите список процессов 
```docker ps```.  
Посмотрите все прослушиваемые порты, должны быть 80, 11211, 9000 
```netstat -plnt```.  
- Сделайте запись в hosts, запустите установку сайта
```
127.0.0.1    domain.com
```

 

## Примечание
- В настройках подключения требуется указывать имя сервиса, например для подключения к mysql нужно указывать "mariadb", а не "localhost".
