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


```

## Контейнеры

```
docker ps -a                        - просмотр контейнеров в системе всех (-a)
docker rm $(docker ps -aq)          - удаление всех контейнеров

```

```
docker start asp                    - пуск контейнера asp

```
