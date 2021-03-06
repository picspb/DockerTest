# DockerTest
Тестирование работы с ДокерХабом

https://www.youtube.com/watch?v=Sa7uOGczoHc&t=490s

## Образы
```
docker images                     - просмотр локальных (скачанных) образов
docker pull alpine                - получить образ alpine Linux из репозитория
docker rmi $(docker images -q)    - удалить все образы

```

```
docker run -it alpine             - запуск образа интерактивно(-i) с терминалом (-t) 
docker run -d alpine              - запуск образа в фоне (-d)
docker run -d --name alp alpine   - запуск образа с именем alp (--name)
docker run -d -p 3000:8080 alpine - запуск c пробросом портов изнутри 8080, снаружи 3000
docker run -it -v c:\YandexDisk:/home/Yandex alpine 
                        - запуск c монтированием внешней папки внутрь запускаемого образа
```

## Контейнеры

```
docker ps -a                        - просмотр контейнеров в системе всех (-a)
docker rm $(docker ps -aq)          - удаление всех контейнеров

```

```
docker start asp                    - пуск контейнера asp
docker exec -it asp bash            - запуск приложения bash внутри контейнера
```

```
docker attach asp                   - подключится к работающему контейнеру
Ctrl+P и сразу Ctrl+Q               - отключиться от работающего контеййнера (не останавливя его работу)
```
## DockerFile
https://www.youtube.com/watch?v=Lu1ziKbQYIQ&t=13s
```
#FROM - из какого образа строим контейнер
FROM alpine

#запускаем нужные нам пакеты. 
#каждый RUN создаёт новый слой, поэтому чтобы не плодить слои, разделяем команды && или \ && 
#здесь ставим NODE.JS - пакет npm и http-server
RUN apk add npm && npm i -g http-server

#создаём каталог /home/server внутри контейнера (точка монтирования)
VOLUME /home/server

#назначаем рабочий каталог /home/server внутри контейнера (ограничиваем видимость)
WORKDIR /home/server

#копируем все файлы из текущего каталога в каталог контейнера /home/server
COPY ./ /home/server/

#открываем порт 8080
EXPOSE 8080

#запускаем http-server
CMD http-server
```
### Сборка образа
```
docker build -t picspb/node:v1 .
docker build -t picspb/pic-web-server-ext:v1 -f Dockerfile.ex .
docker build -t picspb/pic-web-server-int:v1 -f Dockerfile.in .
```
### Запуск образа
```
docker run -it --name node-dru -p 3000:8080 picspb/node:v1
docker run -it --name web-ext -p 3000:3000 picspb/pic-web-server-ext:v1
docker run -it --name web-int -p 3000:3000 picspb/pic-web-server-int:v1
```
### Отправка образа в DockerHub
```
docker push picspb/node:v1
````
### Получение образа с DockerHub
```
docker pull picspb/node:v1
````

