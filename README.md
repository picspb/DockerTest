# DockerTest
Тестирование работы с ДокерХабом

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
docker run -it -v c:\YandexDisk:/home/Yandex alpine - запуск c монтированием внешней папки внутрь запускаемого образа
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
