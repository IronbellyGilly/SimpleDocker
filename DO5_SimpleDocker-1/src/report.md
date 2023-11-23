## Part 1. Готовый докер  
#### 1) Взял официальный докер образ с `nginx` и выкачал его при помощи `docker pull` 
![SimpleDocker](screenshots/Part 1.1.png)

#### 2) Проверил наличие докер образа через `docker images`
![SimpleDocker](screenshots/Part 1.2.png)

#### 3) Запустил докер образ через `docker run -d [image_id|repository]`
![SimpleDocker](screenshots/Part 1.3.png)

#### 4) Проверил, что образ запустился через `docker ps`
![SimpleDocker](screenshots/Part 1.4.png)

#### 5) Посмотрел информацию о контейнере через `docker inspect [container_id|container_name]`
![SimpleDocker](screenshots/Part 1.5.1.png)

![SimpleDocker](screenshots/Part 1.5.2.png)

![SimpleDocker](screenshots/Part 1.5.3.png)

#### 6) Остановил докер образ через `docker stop [container_id|container_name]`

![SimpleDocker](screenshots/Part 1.6.png)

#### 7) Проверил, что образ остановился через `docker ps`
![SimpleDocker](screenshots/Part 1.7.png)

#### 8) Запустил докер с портами 80 и 443 в контейнере, замапленными на такие же порты на локальной машине, через команду `run`
![SimpleDocker](screenshots/Part 1.8.png)

#### 9) Проверил, что в браузере по адресу `localhost:80` доступна стартовая страница `nginx`
![SimpleDocker](screenshots/Part 1.9.png)

#### 10) Перезапустил докер контейнер через `docker restart [container_id|container_name]`
![SimpleDocker](screenshots/Part 1.10.png)

#### 11) Проверил, что контейнер запустился

![SimpleDocker](screenshots/Part 1.11.png)

## Part 2. Операции с контейнером

#### 1) Прочитал конфигурационный файл `nginx.conf` внутри докер контейнера через команду exec
![SimpleDocker](screenshots/Part 2.1.png)

#### 2) Создал на локальной машине файл `nginx.conf`

#### 3) Настроил в нем по пути `/status` отдачу страницы статуса сервера `nginx`
![SimpleDocker](screenshots/Part 2.3.png)

#### 4) Скопировал созданный файл `nginx.conf` внутрь докер образа через команду docker `cp`
![SimpleDocker](screenshots/Part 2.4.png)

#### 5) Перезапустил nginx внутри докер образа через команду `exec`
![SimpleDocker](screenshots/Part 2.5.png)

#### 6) Проверил, что по адресу `localhost:80/status` отдается страничка со статусом сервера `nginx`
![SimpleDocker](screenshots/Part 2.6.png)

#### 7-8) Экспортировал контейнер в файл `container.tar` через команду `export` и остановил контейнер
![SimpleDocker](screenshots/Part 2.7,8.png)

#### 9) Удалил образ через docker `rmi` `[image_id|repository]`, не удаляя перед этим контейнеры
![SimpleDocker](screenshots/Part 2.9.png)

#### 10) Удалил остановленный контейнер
![SimpleDocker](screenshots/Part 2.10.png)
![SimpleDocker](screenshots/Part 2.11.png)

#### 11) Импортировал контейнер обратно через команду `import`
![SimpleDocker](screenshots/Part 2.12.png)

#### 12-13) Запустил импортированный контейнер и проверил, что по адресу `localhost:80/status` отдается страничка со статусом сервера `nginx`
![SimpleDocker](screenshots/Part 2.13.png)


## Part 3. Мини веб-сервер

#### 1) Написал мини сервер на `C` и `FastCgi`
![SimpleDocker](screenshots/Part 3.1.png)

#### 2) Написал свой `nginx.conf`, который будет проксировать все запросы с `81` порта на `127.0.0.1:8080`
![SimpleDocker](screenshots/Part 3.2.png)

#### 3) Перенес созданные файлы:
![SimpleDocker](screenshots/Part 3.3.png)

#### 4) Вошел в контейнер:
![SimpleDocker](screenshots/Part 3.4.png)

#### 5) Запустил написанный мини сервер через `spawn-fcgi` на порту `8080`
![SimpleDocker](screenshots/Part 3.5.png)

#### 6) Проверил, что в браузере по `localhost:81` отдается написанная страница
![SimpleDocker](screenshots/Part 3.6.png)

## Part 4. Свой докер

#### 1) Написал свой докер образ: 
![SimpleDocker](screenshots/Part 4 Dockerfile.png)

#### 2) Собрал написанный докер образ через `docker build`:
![SimpleDocker](screenshots/Part 4 build.png)

#### 3) Проверил через `docker images`, что все собралось корректно
![SimpleDocker](screenshots/Part 4 images.png)

#### 4) Запустил собранный докер образ с маппингом 81 порта на 80 на локальной машине  и маппингом папки `./nginx` внутрь контейнера по адресу, где лежат конфигурационные файлы `nginx'а`:
![SimpleDocker](screenshots/Part 4 map.png)

#### 6) Дописал в `./nginx/nginx.conf` проксирование странички `/status`, по которой надо отдавать статус сервера `nginx`:
![SimpleDocker](screenshots/Part 4 nginx.png)

#### 7) Перезапустил докер образ:
![SimpleDocker](screenshots/Part 4 docker restart.png)

#### 8) Все проверил: 
![SimpleDocker](screenshots/Part 4 check.png)

## Part 5. Dockle

#### 1) Установил `dockle`:
![SimpleDocker](screenshots/Part 5 install dockle.png)

#### 2) Просканировал образ:
![SimpleDocker](screenshots/Part 5 errors.png)

#### 3) Исправил `Dockerfile` так, чтобы не было ошибок:
![SimpleDocker](screenshots/Part 5 Dockerfile.png)

#### 4) Все проверил: 
![SimpleDocker](screenshots/Part 5 buld & check.png)

## Part 6. Базовый Docker Compose

#### 1) Написал файл `docker-compose.yml`:
![SimpleDocker](screenshots/Part 6 docker-compose.png)

#### 2) Переделал `nginx.conf`,для проксирования:
![SimpleDocker](screenshots/Part 6 nginx.png)

#### 3) Собрал и запустил проект:
![SimpleDocker](screenshots/Part 6 building.png)

#### 4) Все проверил: 
![SimpleDocker](screenshots/Part 6 check.png)