# Docker

## Терминология

* **Image** — образ, на основе которого будет запущен контейнер
* **Docker Daemon** — фоновый сервис, который создаёт, запускает и управляет контейнерами
* **Docker Client** — терминальная утилита, позволяющая взаимодействовать с Docker Daemon
* **Docker Hub** — репозиторий с образами

## Команды

### Загрузка образа из репозитория Docker

```bash
docker pull <image_name>
```

### Список загруженных образов

```bash
docker images
```

### Удаление образа

```bash
docker image <image>
```

Удаляет образ с **именем** или **id** `<image>`

### Запуск контейнера

```bash
docker run <image_name> <command>
```

1. **Docker** находит **образ** `<image_name>` и запускает **контейнер** с ним
2. В контейнере выполняется **команда** `<command>`
3. **Контейнер** завершается

Запуск контейнера и работа с ним через `sh`:

```bash
docker run -it <image_name> sh
```

Параметры команды `docker run`:

* `-d` — "открепить" терминал (запуск контейнера в фоновом режиме)
* `-P` — публикация портов
* `-p <port>:<tcp_port>` — запуск контейнера с кастомным портом
* `--name <name>` — задание названия контейнеру
* `--env-file <path>` — путь к файлу с переменными окружения
* `--link <name>:<container_id>` — связь запускаемого контейнера с контейнером `<container_id>` , именуемая `<name>`

Остановка "откреплённого" контейнера:

```bash
docker stop <container_id>
```

### Запуск команды в активном контейнере

```bash
docker exec <container_id> <command>
```

### Список контейнеров

Контейнеры, запущенные в данный момент:

```bash
docker ps
```

История запуска контейнеров:

```bash
docker ps -a
```

### Удаление контейнеров

```bash
docker rm <container_id> <container_id> ...
```

Удаляет контейнеры с **id** `<container_id>`

Удаление неиспользуемых контейнеров:

```bash
docker rm $(docker ps -a -q -f status=exited)
```

### Просмотр портов контейнера

```bash
docker port <name>
```

`<name>` — имя контейнера

### Создание образа

```bash
docker build <path>
```

Создаёт **образ** на основе **Dockerfile**

`<path>` — **директория** или **URL**, по которому расположен **Dockerfile**

Если **Dockerfile** содержит несколько стадий билда, выбрать конкретную стадию можно параметром `--target`:

```bash
docker build --target production-env .
```

### Публикация локального образа в Docker Hub

Перед публикацией нужно войти в систему с помощью `docker login`

```bash
docker push <image_name>
```

## Dockerfile

### FROM

```Dockerfile
FROM <image_name>:<version>
```

Устанавливает базовый **образ** `<image_name>` **версии** `<version>`

### ARG

```Dockerfile
ARG <argument>=<value>
```

**Переменная** с названием `<argument>` и значением `<value>`

Пример использования `ARG`:

```Dockerfile
ARG VERSION=latest
FROM busybox:$VERSION
```

### RUN

```Dockerfile
RUN <command>
```

Запускает внутри контейнера **комманду** `<command>`

По умолчанию используется **оболочка** `/bin/sh -c`

Если команда содержит несколько строк, в конце каждой из них нужно ставить символ `\`

### LABEL

```Dockerfile
LABEL <key>=<value> <key>=<value> ...
```

Добавляет образу метаданные с **ключом** `<key>` и **значеним** `<value>`

Просмотреть метаданные **образа** можно **командой** `docker inspect <image_name>`

### EXPOSE

```Dockerfile
EXPOSE <port>/<protocol>
```

Обозначает **порт**, прослушиваемый контейнером

Эти порты следует указать при выполнении `docker run`

### ENV

```Dockerfile
ENV <key> <value>
ENV <key>=<value> <key>=<value> ...
```

Задаёт переменной **окружения** `<key>` **значение** `<value>`

### CMD

```Dockerfile
CMD ["<executable>","<param>","<param>"]
```

Выполняет **команду** `<executable>`  с **параметром** `<param>`
